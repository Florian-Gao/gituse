---
title: wanmen_py4_np
date: 2019-09-08 22:51:49
tags: 
- python
- wanmen
---
# py4



```python
import numpy as np
```

## 列表转换为数组


```python
a=list(range(10))
b=np.array(a)
print(b)
type(b)
```

    [0 1 2 3 4 5 6 7 8 9]





    numpy.ndarray




```python
np.zeros((4,4),dtype=int)
```




    array([[0, 0, 0, 0],
           [0, 0, 0, 0],
           [0, 0, 0, 0],
           [0, 0, 0, 0]])




```python
b=np.ones((3,4),float)
b
```




    array([[1., 1., 1., 1.],
           [1., 1., 1., 1.],
           [1., 1., 1., 1.]])




```python
np.full((3,3),3.14)
```




    array([[3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14],
           [3.14, 3.14, 3.14]])




```python
np.full_like(b,314)
```




    array([[314., 314., 314., 314.],
           [314., 314., 314., 314.],
           [314., 314., 314., 314.]])




```python
np.zeros_like(b,int)
```




    array([[0, 0, 0, 0],
           [0, 0, 0, 0],
           [0, 0, 0, 0]])



## random



```python
import random
random.randint(5,10)  #randint 5-10随机数
```




    5




```python
#3*3数组  random 0-1随机数
np.random.random((3,3))
```




    array([[0.50325932, 0.2297995 , 0.1392857 ],
           [0.54897845, 0.16455239, 0.29737913],
           [0.13850923, 0.29868182, 0.51995168]])




```python
#5*5数组（形成随机数，经常用到）
np.random.randint(0,10,(5,5))
```




    array([[2, 6, 8, 2, 7],
           [7, 8, 3, 4, 5],
           [8, 9, 2, 6, 0],
           [1, 6, 5, 0, 6],
           [6, 1, 1, 2, 8]])



## 范围取值


```python
list(range(0,10))
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
# np.arrange(begin,end, step)
np.arange(0,10,2)
```




    array([0, 2, 4, 6, 8])




```python
#  np.linspace(初始值，末尾值，个数)
np.linspace(0,3,10)
```




    array([0.        , 0.33333333, 0.66666667, 1.        , 1.33333333,
           1.66666667, 2.        , 2.33333333, 2.66666667, 3.        ])




```python
# 单位矩阵
np.eye(10,dtype=int)
```




    array([[1, 0, 0, 0, 0, 0, 0, 0, 0, 0],
           [0, 1, 0, 0, 0, 0, 0, 0, 0, 0],
           [0, 0, 1, 0, 0, 0, 0, 0, 0, 0],
           [0, 0, 0, 1, 0, 0, 0, 0, 0, 0],
           [0, 0, 0, 0, 1, 0, 0, 0, 0, 0],
           [0, 0, 0, 0, 0, 1, 0, 0, 0, 0],
           [0, 0, 0, 0, 0, 0, 1, 0, 0, 0],
           [0, 0, 0, 0, 0, 0, 0, 1, 0, 0],
           [0, 0, 0, 0, 0, 0, 0, 0, 1, 0],
           [0, 0, 0, 0, 0, 0, 0, 0, 0, 1]])



## 访问数组中元素


```python
# 嵌套列表的元素访问
a=[[1,2,3],[2,3,4],[3,4,5]]
a[1][0]
```




    2




```python
b=np.full((3,3),3,int)
b[0][1]
```




    3




```python
#另一种方法提取元素
b[0,1]
```




    3




```python
#数组切片 取前两行
b[:2]
```




    array([[3, 3, 3],
           [3, 3, 3]])




```python
# 取前两行和前两列
b[:2,:2]
```




    array([[3, 3],
           [3, 3]])




```python
# 取前两行，再取前两行,与b[:2,:2]不一样
b[:2][:2]
```




    array([[3, 3, 3],
           [3, 3, 3]])



## 数组属性


```python
# 维度
print(b.ndim)
# shape  n*n矩阵
print(b.shape)
# size  有多少个数
print(b.size)
# dtype  数据类型
print(b.dtype)
# itemsize  每个树占8个字节
print(b.itemsize)
# nbytes  一共占多少字节，8*9
print(b.nbytes)

```

    2
    (3, 3)
    9
    int64
    8
    72


## np运算


```python
np.full(10,2.3)
```




    array([2.3, 2.3, 2.3, 2.3, 2.3, 2.3, 2.3, 2.3, 2.3, 2.3])




```python
a=np.array([[1,2],[2,4]])
print(np.sum(a))
print(np.sum(a,axis=1))  # 按行求和
```

    9
    [3 6]



```python
np.random.rand(10)  #rand and random is same
```




    array([0.32042186, 0.0939424 , 0.4289252 , 0.35593387, 0.92730687,
           0.28779505, 0.90388186, 0.19089802, 0.29240305, 0.11551011])




```python
#和上面一样
n=np.random.random(10)
```


```python
# timeit 看时间
%timeit sum(n)
```

    1.96 µs ± 23.4 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)



```python
%timeit np.sum(n)
```

    3.51 µs ± 87.2 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)


## bool 比较


```python
a=np.array(range(10))
```


```python
a
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
a>3
```




    array([False, False, False, False,  True,  True,  True,  True,  True,
            True])




```python
a.reshape(2,5)
```




    array([[0, 1, 2, 3, 4],
           [5, 6, 7, 8, 9]])




```python
np.sort(a)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



## 拼接


```python
#0 按行拼接，1按列拼接
a=[[1,2,3],[1,2,3]]
b=[[2,3,4],[2,3,4]]
c=[[3,4,5],[3,4,5]]
np.concatenate([a,b,c],axis=0) #0 按行拼接，1按列拼接
```




    array([[1, 2, 3],
           [1, 2, 3],
           [2, 3, 4],
           [2, 3, 4],
           [3, 4, 5],
           [3, 4, 5]])


