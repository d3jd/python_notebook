# 第15课 - 我的世界: 建筑爆破

## 本课知识点回顾
* 我的世界中**有的方块拥有特殊属性**
    * 比如棉花，TNT炸药方块
* 修改方块的属性可以通过给setBlocks()函数添加一个**额外的参数**做到
    * 比如tnt炸药方块只有在**方块属性参数**是奇数时才可以引爆
    ![](/assets/屏幕快照 2019-05-25 下午12.38.55.png)
* 设计一个**好程序的基本修养**
    * 重复的事情竟可能使用循环
    * 将每个小功能都设计成函数，这样可以重复调用
    * 函数中可变的东西使用参数表达，这样使函数的使用更灵活


## 例子：金字塔（手动版）
写一个能够生成高三层金字塔的程序
![](/assets/屏幕快照 2019-05-25 下午12.46.11.png)
```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

# 获得玩家位置
pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

sand_block = 24

# 生成小金字塔
mc.setBlocks(x - 2, y + 0, z - 2, x + 2, y + 0, z + 2, sand_block)
mc.setBlocks(x - 1, y + 1, z - 1, x + 1, y + 1, z + 1, sand_block)
mc.setBlocks(x - 0, y + 2, z - 0, x + 0, y + 2, z + 0, sand_block)

```

## 例子：自动金字塔
写一个能够生成任意大小金字塔的函数
![](/assets/pyramid.png)
```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()


def pyramid(levels):
    sand_block = 24
    tnt_block = 46

    pos = mc.player.getPos()
    x = pos.x
    y = pos.y
    z = pos.z
    x += levels

    for i in range(levels):
        width = levels - i
        mc.setBlocks(x-width, y+i, z-width, x+width, y+i, z+width, sand_block)

pyramid(10)
```

## 例子：巨型炸药
写一个能够生成任意大小金字塔的函数
![](/assets/tnt_bomb.png)

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

tnt_block = 46

# single tnt block
mc.setBlock(x+1, y+1, z+1, tnt_block, 1)

# tnt cube
mc.setBlocks(x+1, y+1, z+1, x+5, y+5, z+5, tnt_block, 1)
```

## 例子：金字塔爆破
修改之前的金字塔程序，将其金字塔最底层变成TNT方块，其它方块的材料保持不变
![](/assets/pyramid_bomb.png)

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()


def pyramid(levels):
    sand_block = 24
    tnt_block = 46

    pos = mc.player.getPos()
    x = pos.x
    y = pos.y
    z = pos.z
    x += levels

    for i in range(levels):
        width = levels - i
        if i == 0:
            mc.setBlocks(x-width, y+i, z-width, x+width, y+i, z+width, tnt_block, 1)
        else:
            mc.setBlocks(x-width, y+i, z-width, x+width, y+i, z+width, sand_block)

pyramid(10)
```



---
![](/assets/屏幕快照 2019-05-25 下午12.34.21.png)