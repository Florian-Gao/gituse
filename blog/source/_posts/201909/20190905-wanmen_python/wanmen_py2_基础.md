---
title: wanmen_py2_基础
date: 2019-09-06 22:51:49
tags: 
- wanmem
- python
---
# python 下

## 条件判断 if


```python
if condition:
    do
elif condition:
    do 
else:
    do
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-1-ab58e33a4037> in <module>
    ----> 1 if condition:
          2     do
          3 elif condition:
          4     do
          5 else:


    NameError: name 'condition' is not defined


### 断言 assert


```python
age=18
assert age==18
```


```python
age=18
assert age==19 '他竟然不是18'
```


      File "<ipython-input-7-afa90edc5ffb>", line 2
        assert age==19 '他竟然不是18'
                               ^
    SyntaxError: invalid syntax



## 循环 (能使用for，尽量使用for循环)

### for


```python
costs=[1,2,3,4,5]
for cost in costs:
    print('消费{}元'.format(str(cost).center(10)))
```

    消费    1     元
    消费    2     元
    消费    3     元
    消费    4     元
    消费    5     元


### for循环可以加else


```python
a=[2,3,4]

for i in a:
    if i%2==0:
        print('{} is even'.format(i))
    else:
        print('{} is odd'.format(i))
else:
    print('all')
```

    2 is even
    3 is odd
    4 is even
    all


### for 循环构建推导式


```python
a=list(range(10))
a
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
b=[c*10 for c in a]
b
```




    [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]




```python
# 字典推导式
b=[111,222,333]
dict_num={c:d for c in a for d in b}
dict_num
```




    {2: 333, 3: 333, 4: 333}



### while


```python
import random as r

random_numbers=[]
while len(random_numbers)<10:
    random_numbers.append(r.randint(0,10))
print(random_numbers,len(random_numbers))
```

    [3, 6, 10, 9, 5, 4, 8, 2, 9, 7] 10


## continue 跳出本次小循环
## break 跳出整个大循环


```python

```


```python

```

## 函数 def


```python
var={
    'a':100,
    'b':100,
    'c':200
}
#注意要有括号框起来，否则运行不起来
[key for key, value in var.items() if value==100]
```




    ['a', 'b']




```python
#函数调用
def get_keys(va,value):
    return [k for k,v in va.items() if v==value]
get_keys(var,200)
```




    ['c']




```python
get_keys({'a':10},10)
```




    ['a']



## 不建议在函数内对可变类型进行更改，建议用函数返回值进行更改，<font color='red'>列表可变</font>，<font color='green'>变量，元组不可变</font>

## 参数的收集


```python
def test(name,age,*args,**keys):# *args 收集位置参数， **keys收集关键字参数
    print(name,age,*args,**keys)
test('Tom',18,28,[1,28])  #如果没有*args，后面的那些数字会形成一个元组 如果没有**keys，就会在后面又出现一个空字典{}
```

    Tom 18 28 [1, 28]



```python
test('Bob',17,var)
```

    Bob 17 {'a': 100, 'b': 100, 'c': 200}



```python
import random
round(random.random(),3)
```




    0.834



# python 装饰器 


```python
@decorator
# 等同于f=decorator(test)
def test():
    return random.random()
@decorator
def test_2():
    return random.random()*10
```


```python
def decorator(func):
    def wrapper(*args,**k):
        return round(func(*args,**k),3)
    return wrapper
```


```python
test()
```




    0.324




```python
test_2()
```




    7.428



# 类


```python
class Person:
    
    def __init__(self, name, age):
        self._name=name
        self._age=age
        
    #初始化函数中，self后面的是实例化对象的属性，加下划线的意思是，代表这个属性是私有的，不应该访问
    
    def get_name(self):
        return self._name
    
    def get_age(self):
        return self._age
    
    def rename(self,new_name):
        self._name=new_name

```

## 初始化函数中，self后面的是实例化对象的属性，加下划线的意思是，代表这个属性是私有的，不应该访问


```python
p=Person('gao',12)
```


```python
p.get_name()
```




    'gao'




```python
p.get_age()
```




    12




```python
p.rename('wang')
```


```python
p.get_name()
```




    'wang'



# 类里面套用类


```python
class Student(Person):
    def set_score(self,score):
        self._score=score
        
        
    def get_score(self):
        return self._score

```


```python
s=Student('gao',12)
```


```python
s.get_name()
```




    'gao'




```python
s.get_age()
```




    12




```python
s.set_score(100)
```


```python
s.get_score()
```




    100


