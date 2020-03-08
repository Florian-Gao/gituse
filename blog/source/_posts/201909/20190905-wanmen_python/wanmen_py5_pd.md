---
title: wanmen_py5_pd
date: 2019-09-09 22:51:49
tags: 
- wanmen
- python
---
# pandas

- 新的数据格式 .csv
- 纯文本
- 每条记录被分隔符分隔为字段
- 每条记录都有同样的字段序列


```python
import pandas as pd
```


```python
#df=pd.read_csv('路径')
df=pd.read_csv('/Users/Florian_Gao/Desktop/git/github/wanmen-python/modol.csv', sep=',') # sep 分隔符格式
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>赵</td>
      <td>女</td>
      <td>111</td>
      <td>123</td>
      <td>124</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>孙</td>
      <td>女</td>
      <td>124</td>
      <td>145</td>
      <td>143</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>兰</td>
      <td>男</td>
      <td>122</td>
      <td>133</td>
      <td>144</td>
    </tr>
  </tbody>
</table>
</div>




```python
#打印几行
df.head(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
    </tr>
  </tbody>
</table>
</div>




```python
type(df)
```




    pandas.core.frame.DataFrame




```python
#列名
print(df.columns)
#索引
print(df.index)
```

    Index(['序号', '姓名', '性别', '语文', '数学', '英语'], dtype='object')
    RangeIndex(start=0, stop=5, step=1)



```python
# 第0行
df.loc[0]
```




    序号      1
    姓名      高
    性别      男
    语文    120
    数学    110
    英语    130
    Name: 0, dtype: object



## 筛选


```python
# the first column is 序号
df.columns[0]
```




    '序号'




```python
df.数学>3
```




    0    True
    1    True
    2    True
    3    True
    4    True
    Name: 数学, dtype: bool




```python
df[df.数学>3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>赵</td>
      <td>女</td>
      <td>111</td>
      <td>123</td>
      <td>124</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>孙</td>
      <td>女</td>
      <td>124</td>
      <td>145</td>
      <td>143</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>兰</td>
      <td>男</td>
      <td>122</td>
      <td>133</td>
      <td>144</td>
    </tr>
  </tbody>
</table>
</div>



## 复杂筛选


```python
# 语文<4，数学>2
df[(df.语文<4)&(df.数学>2)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>



## 排序


```python
#先按数学排序，再按语文排序
df.sort_values(['数学','语文'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>赵</td>
      <td>女</td>
      <td>111</td>
      <td>123</td>
      <td>124</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>兰</td>
      <td>男</td>
      <td>122</td>
      <td>133</td>
      <td>144</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>孙</td>
      <td>女</td>
      <td>124</td>
      <td>145</td>
      <td>143</td>
    </tr>
  </tbody>
</table>
</div>



## 访问


```python
#按索引位  第四行  /0 1 2 3
df.loc[3]
```




    序号      4
    姓名      孙
    性别      女
    语文    124
    数学    145
    英语    143
    Name: 3, dtype: object



## 索引


```python
scores={
    'Name':['gao','li','wang'],
    'English':[120,110,130],
    'Math':[122,132,143]
}
dp=pd.DataFrame(scores,index=['one','two','three']) # 这里自己制定的索引形式
dp
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>gao</td>
      <td>120</td>
      <td>122</td>
    </tr>
    <tr>
      <th>two</th>
      <td>li</td>
      <td>110</td>
      <td>132</td>
    </tr>
    <tr>
      <th>three</th>
      <td>wang</td>
      <td>130</td>
      <td>143</td>
    </tr>
  </tbody>
</table>
</div>




```python
dp.index
```




    Index(['one', 'two', 'three'], dtype='object')




```python
#dp.loc[1]  #此时索引位0ne，two，three
dp.loc['one']
```




    Name       gao
    English    120
    Math       122
    Name: one, dtype: object




```python
dp.iloc[0]  #这个就可以实现不按index进行操作
```




    Name       gao
    English    120
    Math       122
    Name: one, dtype: object




```python
#合并loc和iloc
dp.ix[0]
```

    /Users/Florian_Gao/anaconda3/lib/python3.7/site-packages/ipykernel_launcher.py:2: DeprecationWarning: 
    .ix is deprecated. Please use
    .loc for label based indexing or
    .iloc for positional indexing
    
    See the documentation here:
    http://pandas.pydata.org/pandas-docs/stable/indexing.html#ix-indexer-is-deprecated
      





    Name       gao
    English    120
    Math       122
    Name: one, dtype: object




```python
# 也可进行切片，打印前两行
dp.iloc[:2]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>gao</td>
      <td>120</td>
      <td>122</td>
    </tr>
    <tr>
      <th>two</th>
      <td>li</td>
      <td>110</td>
      <td>132</td>
    </tr>
  </tbody>
</table>
</div>




```python
#访问某一行，是错误的
#dp[0]
#访问前两行就可以,可以使用切片
dp[:2]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
      <th>math classify</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>gao</td>
      <td>120</td>
      <td>122</td>
      <td>good</td>
    </tr>
    <tr>
      <th>two</th>
      <td>li</td>
      <td>110</td>
      <td>132</td>
      <td>very good</td>
    </tr>
  </tbody>
</table>
</div>




```python
dp.Math.values
```




    array([122, 132, 143])




```python
#简单技术
dp.Math.value_counts()
```




    143    1
    122    1
    132    1
    Name: Math, dtype: int64



# <font color='red'>重点</font>


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
      <th>new_line</th>
      <th>math classify</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
      <td>keep going</td>
      <td>keep going</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
      <td>good</td>
      <td>good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>赵</td>
      <td>女</td>
      <td>111</td>
      <td>123</td>
      <td>124</td>
      <td>good</td>
      <td>good</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>孙</td>
      <td>女</td>
      <td>124</td>
      <td>145</td>
      <td>143</td>
      <td>very good</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>兰</td>
      <td>男</td>
      <td>122</td>
      <td>133</td>
      <td>144</td>
      <td>very good</td>
      <td>very good</td>
    </tr>
  </tbody>
</table>
</div>




```python
def func(score):
    if score>=130:
        return 'very good'
    elif score>=120:
        return 'good'
    else:
        return 'keep going'
#dp['math classify']=dp.Math.map(func)
df['math classify']=df.数学.map(func)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>序号</th>
      <th>姓名</th>
      <th>性别</th>
      <th>语文</th>
      <th>数学</th>
      <th>英语</th>
      <th>new_line</th>
      <th>math classify</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>高</td>
      <td>男</td>
      <td>120</td>
      <td>110</td>
      <td>130</td>
      <td>keep going</td>
      <td>keep going</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>李</td>
      <td>男</td>
      <td>110</td>
      <td>129</td>
      <td>131</td>
      <td>good</td>
      <td>good</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>赵</td>
      <td>女</td>
      <td>111</td>
      <td>123</td>
      <td>124</td>
      <td>good</td>
      <td>good</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>孙</td>
      <td>女</td>
      <td>124</td>
      <td>145</td>
      <td>143</td>
      <td>very good</td>
      <td>very good</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>兰</td>
      <td>男</td>
      <td>122</td>
      <td>133</td>
      <td>144</td>
      <td>very good</td>
      <td>very good</td>
    </tr>
  </tbody>
</table>
</div>



## 同样的，用apply也可以实现增加一行


```python
#多列形成一个新列
dp['new_score']=dp.apply(lambda x: x.Math+ x.English,axis=1)
dp
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
      <th>math classify</th>
      <th>new_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>gao</td>
      <td>120</td>
      <td>122</td>
      <td>good</td>
      <td>242</td>
    </tr>
    <tr>
      <th>two</th>
      <td>li</td>
      <td>110</td>
      <td>132</td>
      <td>very good</td>
      <td>242</td>
    </tr>
    <tr>
      <th>three</th>
      <td>wang</td>
      <td>130</td>
      <td>143</td>
      <td>very good</td>
      <td>273</td>
    </tr>
  </tbody>
</table>
</div>




```python
#前两行
dp.head(2)
#后两行
dp.tail(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
      <th>math classify</th>
      <th>new_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>li</td>
      <td>110</td>
      <td>132</td>
      <td>very good</td>
      <td>242</td>
    </tr>
    <tr>
      <th>three</th>
      <td>wang</td>
      <td>130</td>
      <td>143</td>
      <td>very good</td>
      <td>273</td>
    </tr>
  </tbody>
</table>
</div>



# 全局使用，以及lambda函数使用


```python
# x 表示所有元素
dp.applymap(lambda x: '%'+str(x)+ '%')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>English</th>
      <th>Math</th>
      <th>math classify</th>
      <th>new_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>%gao%</td>
      <td>%120%</td>
      <td>%122%</td>
      <td>%good%</td>
      <td>%242%</td>
    </tr>
    <tr>
      <th>two</th>
      <td>%li%</td>
      <td>%110%</td>
      <td>%132%</td>
      <td>%very good%</td>
      <td>%242%</td>
    </tr>
    <tr>
      <th>three</th>
      <td>%wang%</td>
      <td>%130%</td>
      <td>%143%</td>
      <td>%very good%</td>
      <td>%273%</td>
    </tr>
  </tbody>
</table>
</div>



## 匿名函数


```python
def func(x):
    return x+100

```


```python
list(map(func,range(10)))
```




    [100, 101, 102, 103, 104, 105, 106, 107, 108, 109]


