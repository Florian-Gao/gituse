---
title: Multiprocessing/多进程
date: 2019-09-04 21:21:20
tags: python
---

![multiprocessing](/images/multiprocessing.png)


### import 
```
import multiprocessing as mp
import threading as td
```

#### 定义一个被线程和进程调用的函数
```
def job(a,d)
    print('aaaa')
```

#### 创建线程和进程
注意：Thread和Process的首字母都要大写，被调用的函数没有括号，被调用的函数的参数放在args(…)中
```
t1=td.Thread(target=job,args=(1,2))
p1 = mp.Process(target=job,args=(1,2))
```

#### 启动线程和进程
```
t1.start()
p1.start()
```

#### 分别连接线程和进程
```
t1.join()
d1.join()
```


#### full code

```
import multiprocessing as mp
import threading as td

def job(a,d):
    print('aaaaa')

t1 = td.Thread(target=job,args=(1,2))
p1 = mp.Process(target=job,args=(1,2))
t1.start()
p1.start()
t1.join()    # 分别连接线程和进程
p1.join()
```

#### use
```
if __name__='__main__'
```

```
import multiprocessing as mp

def job(a,d):
    print('aaaaa')

if __name__=='__main__':
    p1 = mp.Process(target=job,args=(1,2))
    p1.start()
    p1.join()
```

### Queen #use to store process
```
import multiprocessing as mp

def job(q):
    res=0
    for i in range(1000):
        res+=i+i**2+i**3
    q.put(res)    #queue  put data in queen

if __name__=='__main__':
    q = mp.Queue()
    p1 = mp.Process(target=job,args=(q,))
    p2 = mp.Process(target=job,args=(q,))
    p1.start()
    p2.start()
    p1.join()
    p2.join()
    res1 = q.get()   #get  the data
    res2 = q.get()
    print(res1+res2)

```


### multiprocessing and threading compare
```
import multiprocessing as mp
import threading as td
import time

def job(q):
    res = 0
    for i in range(1000000):
        res += i+i**2+i**3
    q.put(res) # queue

def multicore():
    q = mp.Queue()
    p1 = mp.Process(target=job, args=(q,))
    p2 = mp.Process(target=job, args=(q,))
    p1.start()
    p2.start()
    p1.join()
    p2.join()
    res1 = q.get()
    res2 = q.get()
    print('multicore:' , res1+res2)

def normal():
    res = 0
    for _ in range(2):
        for i in range(1000000):
            res += i+i**2+i**3
    print('normal:', res)

def multithread():
    q = mp.Queue()
    t1 = td.Thread(target=job, args=(q,))
    t2 = td.Thread(target=job, args=(q,))
    t1.start()
    t2.start()
    t1.join()
    t2.join()
    res1 = q.get()
    res2 = q.get()
    print('multithread:', res1+res2)

if __name__ == '__main__':
    st = time.time()
    normal()
    st1= time.time()
    print('normal time:', st1 - st)
    multithread()
    st2 = time.time()
    print('multithread time:', st2 - st1)
    multicore()
    print('multicore time:', time.time()-st2)
finally, we find multicore is the fastest, multithread is the slowest
```


### Pool #the processing pool
`pool will get a return value, but process can't get the return value.'
pool call the core of CPU, the parameter of processing can design the core's number of CPU

```
import multiprocessing as mp

def job(x):
    return x*x

def multicore():
    pool = mp.Pool(processes=2)  # define the pool, the num in braket(括号) is the core's num
    res = pool.map(job, range(10)) # return results
    print(res)  #[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    res = pool.apply_async(job, (2,))   
    #this way can only get one result, and it will be put in only one core to calculate,  attention ,there is a comma（逗号）
    print(res.get())
    multi_res =[pool.apply_async(job, (i,)) for i in range(10)]   #put into iterator  
    print([res.get() for res in multi_res])  # get from the iterator

if __name__ == '__main__':
    multicore()
```


### share memory  (共享内存)

#### shared value
```
import multiprocessing as mp

value1 = mp.Value('i', 0) 
value2 = mp.Value('d', 3.14)
# i、d 是设置数据类型的，i代表带符号的整型，d代表双精度浮点类型

```
#### shared array
```
array = mp.Array('i', [1, 2, 3, 4])   # is right

array = mp.Array('i', [[1, 2], [3, 4]]) # 2维list
"""
TypeError: an integer is required
"""
## Array is different from numpy, it only be one dimensional, can't be multi-dimensional
```

### parametric data form

![参数数据形式](/images/参数数据形式.png)


### processing lock

#### no lock 
```
import multiprocessing as mp
import time

def job(v, num):
    for _ in range(5):
        time.sleep(0.1) # 暂停0.1秒，让输出效果更明显
        v.value += num # v.value获取共享变量值
        print(v.value, end="")
        
def multicore():
    v = mp.Value('i', 0) # 定义共享变量
    p1 = mp.Process(target=job, args=(v,1))
    p2 = mp.Process(target=job, args=(v,3)) # 设定不同的number看如何抢夺内存
    p1.start()
    p2.start()
    p1.join()
    p2.join()
    
if __name__ == '__main__':
    multicore()
    
```
the result/ process 1 and  process 2  battle for the shared memory
```
1
4
5
8
9
12
13
16
17
20
```
#### if we add process lock ## l=mp.lock()
```
def job(v, num, l):
    l.acquire() # 锁住
    for _ in range(5):
        time.sleep(0.1) 
        v.value += num # 获取共享内存
        print(v.value)
    l.release() # 释放

def multicore():
    l = mp.Lock() # 定义一个进程锁
    v = mp.Value('i', 0) # 定义共享内存
    p1 = mp.Process(target=job, args=(v,1,l)) # 需要将lock传入
    p2 = mp.Process(target=job, args=(v,3,l)) 
    p1.start()
    p2.start()
    p1.join()
    p2.join()

if __name__ == '__main__':
    multicore()
```
the result #when p 1 is done, p 2 begins
```
1
2
3
4
5
8
11
14
17
20
```
























