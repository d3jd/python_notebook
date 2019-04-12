# 第11课-我的世界

## 本课知识点回顾

* **《我的世界》**是什么？
    * 一款可以**自由创造**的**沙盒游戏**
    * 自由创造：可以自由改造世界，没有太多限制
    * 沙盒游戏：不怕犯错，可以反复实验
* 学习目标
    * 用python控制游戏，将需要人重复做的东西自动化
    ![](/assets/图片 2.png)
* 世界的构成
    * 世界由**方块**和**坐标系**构成
    * 方块是组成世界的基本单元
    * 坐标系是确定每个方块位置的方法
* 坐标系有什么用？
    * 坐标系可以在空间中表示物体的位置
    * 2D坐标系例子：地图，2D游戏，做操的队列
    * 3D坐标系例子：3D模型，3D动画，3D游戏
    * **《我的世界》使用的是3D坐标系**
        * **x轴** 代表 前进 或 后退
        * **y轴** 代表 上 或 下
        * **z轴** 代表 左 或 右
![](/assets/图片 1.png)
* 游戏中的几个基本函数
    * **postToChat()** : 在屏幕上显示信息
    * **setPos() **: 更改玩家的位置

## 例子：和我的世界建立连接

```python
# 导入 minecraft 模块
from mcpi.minecraft import Minecraft

# 连接到 minecraft
mc = Minecraft.create()

```

## 例子：改变玩家的位置（瞬间移动）
```python
# 导入 minecraft 模块
from mcpi.minecraft import Minecraft

# 连接到 minecraft
mc = Minecraft.create()

# 设置玩家坐标的变量
x = 10 # 前后
y = 110 # 上下
z = 12 # 左右

# 改变玩家位置
mc.player.setPos(x, y, z)

```


## 例子：多点间瞬间移动

```python

from mcpi.minecraft import Minecraft

mc = Minecraft.create()

while True:
    points = int(input("Enter your points: "))
    if points == 1:
        mc.player.setPos(32, 18, -38)
    elif points == 2:
        mc.player.setPos(60, 20, 32)
    elif points == 3:
        mc.player.setPos(120, 10, 120)
    elif points == 4:
        mc.player.setPos(0, 35, 20)
    else:
        mc.postToChat("try again！")

    mc.postToChat("Done！")

```



## 例子：每隔一秒随机移动位置
```python
from mcpi.minecraft import Minecraft
import random
import time

# 定义随机位置函数
def random_position():
    x = random.randint(-125, 125)
    y = random.randint(-64, 64)
    z = random.randint(-125, 125)
    mc.player.setPos(x, y, z)

# 连接到 minecraft
mc = Minecraft.create()

# 每隔一秒移动到随机位置
count = 0
while count < 10:
    random_position()
    count += 1
    time.sleep(1)


```



---
![](/assets/幻灯片58.jpeg)