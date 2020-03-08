---
title: wanmen_py1_基础
date: 2019-09-05 22:51:49
tags: 
- wanmen
- python
---

### floor 向下取整
### ceil 向上取整

## 增强的格式化字符串函数 format

## 增强的格式化字符串函数 format


```python
import math
```


```python
apple_cost = 10
```


```python
'苹果的花费为：{}'.format(apple_cost)
```




    '苹果的花费为：10'



## 变量类型
- 字符串 str
- 数字 int float complex
- 列表 list
- 元组 tuple
- 字典 dic


```python
#乘方，开方
math.pow(3,10)
```




    59049.0




```python
3**10

```




    59049




```python
#向下取整
math.floor(2.33)
```




    2




```python
# 向上取整
math.ceil(2.33)
```




    3




```python
# 度的转换
math.radians(180)
```




    3.141592653589793




```python
# sin
math.sin(math.pi/2)
```




    1.0




```python
# max min
max(1,2,3)
```




    3




```python
#sum
sum([10,19,20])
```




    49




```python
#divmod()
divmod(10,4)
```




    (2, 2)



## bool 型


## 表格样式（md格式） 
## 对齐用 ：

| 操作符 | 解释 |
| --- | --- |
| < | 小于 |

## 切片

### 字符串不允许变换


```python
list= 'adsfgh jkl'
```


```python
#间隔取字符
list[0:20:2]
```




    'asg k'




```python
#取后5个字符
list[-5:]
```




    'h jkl'




```python
#翻转字符
list[::-1]
```




    'lkj hgfsda'




```python
# 不支持变换
list[-1]=q
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-11-560b81b97c50> in <module>
          1 # 不支持变换
    ----> 2 list[-1]=q
    

    NameError: name 'q' is not defined


## 查看函数用法


```python
list.capitalize?

```


```python
#不加%，就是空格输出
list.center(20,'%')
```




    '%%%%%adsfgh jkl%%%%%'




```python
list.count('a')
```




    1



## 首位字符串以其结尾或开头


```python
list.startswith('abs')
```




    False




```python
list.endswith('abs')
```




    False




```python
list

```




    'adsfgh jkl'




```python
#查找
list.find('a')
```




    0




```python
list.index('a')
```




    0




```python
# 去除空格  strip
# 左侧空格 lstrip
line='     abd'
line.strip()
```




    'abd'




```python
list.upper()
```




    'ADSFGH JKL'




```python
list.lower()
```




    'adsfgh jkl'




```python
list.istitle()
```




    False




```python
list.isupper()
```




    False




```python
list='     absddfff    '
```


```python
list.strip()
```




    'absddfff'




```python
#只去掉左边
list.lstrip()
```




    'absddfff    '



# 列表


```python
# 空列表
a=[1,2]
```

## 可以容纳任意类型的对象，任意数量的对象

# 列表是可变的，字符串是不可变的

## python 是一种动态类型语言，一个变量是什么类型，要看程序在运行过程中变量所代表的🈯️是什么


```python
var=[10,2,3,4]
type(var)
```




    list




```python
var+[10]
```




    [10, 2, 3, 4, 10]



## 字符串和列表是一种容器型序列，字符串是扁平型序列


```python
a=[1,2]
b=[3,4]
a+b
```




    [1, 2, 3, 4]




```python
a.extend(b)
a
```




    [1, 2, 3, 4]




```python
4 in a
```




    True



# tuple 元组 （不可变）


```python
var=()
```


```python
var=tuple()
```


```python
type(var)
```




    tuple




```python
var=(1,2,3,[1,2])
```


```python
#如果一个元素元组
a=(1)
type(a)
```




    int




```python
# 发现上面的不可以，怎么办,下面的方法
a=(1,)
type(a)
```




    tuple



# dic 字典


```python
var={}
```


```python
var=dict()
```


```python
type(var)
```




    dict




```python
var={
    '中':100,
    '左':200
}
```


```python
var
```




    {'中': 100, '左': 200}



## 拉锁函数(zip)


```python
a= [1,2,3]
b= [2,3,4]
```


```python
c= dict(zip(a,b))
c
```




    {1: 2, 2: 3, 3: 4}




```python
c.fromkeys?
```


```python
c.keys()
```




    dict_keys([1, 2, 3])




```python
c.values()
```




    dict_values([2, 3, 4])




```python
c.popitem?
```


```python
c.items()
```




    dict_items([(1, 2), (2, 3), (3, 4)])


