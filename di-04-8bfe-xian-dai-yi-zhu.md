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
例子：创建一个**能画正放形的函数**
```python
import turtle
def draw_square():
    for i in range(4):
        turtle.forward(150)
        turtle.right(90)
```
例子：调用函数，画出正方形
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


### turtle 和 random 综合使用例子

**例子：现代艺术**：

```python
# 导入模块
import turtle
import random

# 随机选取颜色函数
def random_color():
  red = random.randint(0, 255)
  green = random.randint(0, 255)
  blue = random.randint(0, 255)
  turtle.color(red, green, blue)

# 随机选择位置函数
def random_place():
  turtle.penup()
  x = random.randint(-100, 100)
  y = random.randint(-100, 100)
  turtle.goto(x, y)
  turtle.pendown()

# 随机选择乌龟朝向函数
def random_direction():
    angle = random.randint(0,360)
    turtle.setheading(angle)

# 画随机大小的正放形函数
def draw_square():
    n = random.randint(10,100)
    for i in range(4):
        turtle.forward(n)
        turtle.right(90)

# 设置turtle的形状
turtle.shape("turtle")
# 设置turtle的速度（0是最快，1-10之间逐渐变快）
turtle.speed(0)
# 设置turtle的颜色模式（这里参数永远是255）
turtle.colormode(255)

# 画很多正方形
turtle.clear() #清空屏幕
for index in range(10):
    random_color()
    random_place()
    turtle.begin_fill()
    draw_square()
    turtle.end_fill()

# 画很多乌龟
turtle.clear() #清空屏幕
for index in range(30):
    random_color()
    random_place()
    random_direction()
    turtle.stamp()
```


---
![](/assets/第04课_现代艺术.jpg)