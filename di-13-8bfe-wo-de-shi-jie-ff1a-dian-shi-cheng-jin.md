# 第13课 - 我的世界: 点石成金

## 本课知识点回顾

* 我的世界中的四个基本函数：
    * **获取玩家位置：**mc.player.getPos()
    * **设置玩家位置：** mc.player.setPos(x, y, z)
    * **获取方块类型：**mc.getBlock()
    * **放置方块：**mc.setBlock(x, y, z, block)


## 例子：获得玩家坐标

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

print(x, y ,z)

```

## 例子：如影随形
使用while循环每隔5秒在玩家身边10格内生成15个黄金方块


```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

import random
import time

pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

count = 0
while True:
    blocks = [57, 41, 22, 42, 103]
    block = random.choice(blocks)

    mc.setBlock(x + 3, y, z, block)

    count += 1
    time.sleep(1)

    if (block == 41):
        break

mc.postToChat(count)

```

## 例子：巨型方块
不停地在玩家头顶创造巨大的方块（6 x 6 x 6)

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

block = 41 #使用黄金方块

while True:
    # 获得玩家位置
    pos = mc.player.getPos()
    x = pos.x
    y = pos.y
    z = pos.z

    # 将生成位置设为头顶5格处
    y += 5

    # 利用多重循环生成大方块
    for i in range(x-3, x+3):
        for j in range(y-3, y+3):
            for k in range(z-3, z+3):
                mc.setBlock(x + i, y + j, z + k, block)


```


---
![](/assets/hw_13.png)