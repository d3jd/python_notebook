# 第03课-绘图神龟

## 本课知识点回顾

* **模式 (pattern)** 是什么？
    * 事物内在的规律
* **模块识别**是什么？
    * 发现事物内在的规律
* **算法**是什么？
    * 设计程序运行的规则，让程序自动生成结果
* 如何让程序**看起来更自然**（更难被找到规律）？
    * 使用**随机（random)**
* 如何减少重复劳动并让程序思路更清晰？
    * 使用**函数（function)**
    * 创建函数又叫做定义函数**（define a function)**

### 函数的用法
例子：创建一个能画正放形的函数
```python
import turtle
def draw_square():
    for i in range(4):
        turtle.forward(150)
        turtle.right(90)
```
例子：调用函数
```python
draw_square()
```


### random 模块的用法

导入模块：
```python
import random
```
随机获得一个 **0至255之间的整数**：
```python
import random
x = random.randint(0, 255)
```

使turtle **随机前进 x 步**：
```python
import turtle
import random

x = random.randint(0, 255)
turtle.forward(x)
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
![](/assets/屏幕快照 2018-12-15 上午11.20.45.png)