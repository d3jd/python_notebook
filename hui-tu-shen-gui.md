# 第03课-绘图神龟

## 本课知识点回顾

* 函数是什么？
    * 函数的定义：一些指令的集合
    * 调用函数：即使用函数。相当于按顺序执行函数中预先写好的指令。
* 模块是什么？
    * 模块的定义：一些函数的集合
    * 使用模块：import + 模块名字（例子：import turtle)
* 模块与魔法世界类比：
    * 魔法图书馆 = Python 编程语言
    * 魔法书 = 模块
    * 魔法 = 函数
* for in 循环：
    * 循环是重复执行一段指令的方法
    * 写法：
    ```python
    for index in range(4):
        print("Hello World!")
    ```
    * 解释：
        * index: 一个记录现在循环到第几次的循环
        * range(4): 括号中的数字表示重复几次
        * print(): 在这个例子中要重复执行的指令




### Turtle 模块的使用方法

导入模块：
```python
import turtle
```

turtle **前进 100步**：
```python
turtle.forward(100)
```

turtle **后退 100步**：
```python
turtle.back(100)
```

turtle **左转 90度**：
```python
turtle.left(90)
```

turtle **右转 90度**：
```python
turtle.right(90)
```

### Turtle 模块例子

turtle **画正放形**：
```python
for index in range(4):
    forward(100)
    right(90)
```
turtle **画三角形**：
```python
for index in range(3):
    forward(100)
    right(120)
```

turtle **画n边形**：
```python
n = 20
for index in range(n):
    forward(30)
    right(360 / n)
```


---

## 课后作业 1: 背单词

在本子上将以下单词的**中文抄一遍，英文抄十遍，并且做到会背**

中文 | 英文
--- | ---
导入 | import
循环 | loop
函数 | function
索引 | index
范围 | range


## 课后作业 2: 编程题
自己设计一系列指令，通过计算把a b c d从一开始的数值变成最后的数值
必须用到以下所有的计算符号：


```python
+  -  *  /  +=   -=  //  **
```


开始的数值
a = 1
b = 2
c = 3
d = 4

程序结束时的数值

变量 | 数值
--- | ---
a | 10
b | 9
c | 8
d | 7




