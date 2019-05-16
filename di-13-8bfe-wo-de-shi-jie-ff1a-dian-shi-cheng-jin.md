# 第13课 - 我的世界: 点石成金

## 本课知识点回顾

* 之前学过的我的世界中的四个基本函数：
    * **获取玩家位置：**mc.player.getPos()
    * **设置玩家位置：** mc.player.setPos(x, y, z)
    * **获取方块类型：**mc.getBlock()
    * **放置方块：**mc.setBlock(x, y, z, block)
* 虚拟世界（比如3D游戏）运行的基本机制：
    * 每个游戏都由一个巨大的无限循环组成
    * 循环由三个部分组成
        * 事件发生（发球，发射子弹，被击中）
        * 更新游戏（修改生命值，修改弹药数）
        * 渲染画面 （将画面画在屏幕上）
    * 游戏的很多功能（比如发球，被子弹击中）都依赖于一个重要的概念：**碰撞检测**
    ![](/assets/屏幕快照 2019-05-06 下午6.02.28.png)
    * **碰撞检测**：检测两个物体是否碰到了
* 我的世界中进行碰撞检测的函数
    * **mc.events.pollBlockHits()**
    ![](/assets/屏幕快照 2019-05-06 下午6.02.14.png)

## 例子：pollBlockHits() 的使用方法
将剑（鼠标右键）击中的方块变成金子

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

while True:
    hits = mc.events.pollBlockHits()
    for hit in hits:
        mc.setBlock(hit.pos.x, hit.pos.y, hit.pos.z, 41)
```

## 例子：如影随形
使用while循环每隔5秒在玩家身边10格内生成15个黄金方块


```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

import random
import time

block = 41 # 黄金方块

while True:
    # 获得玩家位置
    pos = mc.player.getPos()
    x = pos.x
    y = pos.y
    z = pos.z

    # 在玩家附近生成15个方块
    for i in range(15):
        # 随机生成玩家附近的位置
        x_range = random.randint(-10, 10)
        y_range = random.randint(-10, 10)
        z_range = random.randint(-10, 10)

        # 生成方块
        mc.setBlock(x + x_range, y + y_range, z + z_range, block)

    time.sleep(5)


```

## 例子：巨型方块
不停地在玩家头顶创造巨大的方块（6 x 6 x 6)

```python
from mcpi.minecraft import Minecraft
import time
mc = Minecraft.create()

block = 41 #使用黄金方块

while True:
    # 获得玩家位置
    pos = mc.player.getTilePos()
    x = pos.x
    y = pos.y
    z = pos.z

    # 将生成位置设为头顶3格处
    y += 3

    # 利用多重循环在玩家头顶生成大方块
    for i in range(6):
        for j in range(6):
            for k in range(6):
                mc.setBlock(x + i, y + j, z + k, block)
    time.sleep(1)


```


---
![](/assets/hw_13.png)