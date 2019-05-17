# 第14课 - 我的世界: 自动建筑

## 本课知识点回顾

* 调用函数就是执行函数中预先写好的指令
* **无参数函数**
    ![](/assets/屏幕快照 2019-05-17 下午5.03.48.png)
    * 每次调用函数，只能按同样的方式生成结果
    
* **有参数的函数**
    ![](/assets/屏幕快照 2019-05-17 下午5.03.57.png)
    * 我们可以从外部给函数提供一些线索
    * 这些线索叫做参数
    * 有参数的函数比无参数的函数使用起来更灵活
    * 参数可以不只一个（比如坐标就由x,y,z三个参数组成）
* 新的我的世界函数：**mc.setBlocks(a, b, c, x, y, z, block)**
    * 功能：通过两个顶点的坐标来生成一个多个方块的大长方体
    ![](/assets/屏幕快照 2019-05-17 下午5.05.03.png)


## 例子：巨型方块
当程序运行时，在玩家面前生成一个 10x10x10 的巨大的方块

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

mc.setBlocks(x+1, y+1, z+1, x+11, y+11, z+11, 57)

```

## 例子：自动生成树木
在玩家面前自动生成一颗树的函数
![](/assets/屏幕快照 2019-05-17 下午5.09.34.png)

```python
from mcpi.minecraft import Minecraft
mc = Minecraft.create()

# 函数：种树
def tree(x, y, z, block):
    # 树干
    mc.setBlocks(x, y, z, x, y + 5, z, 17)

    # 树叶
    mc.setBlocks(x - 3, y + 5, z - 3, x + 3, y + 5, z + 3, block)
    mc.setBlocks(x - 2, y + 6, z - 2, x + 2, y + 6, z + 2, block)
    mc.setBlocks(x - 1, y + 7, z - 1, x + 1, y + 7, z + 1, block)

# 获得玩家位置
pos = mc.player.getPos()
x = pos.x
y = pos.y
z = pos.z

# 制造一片森林（简单版）
tree(x + 1, y, z, 41)
tree(x + 5, y, z, 18)
tree(x + 9, y, z, 46)

```


---
![](/assets/屏幕快照 2019-05-17 下午5.09.44.png)