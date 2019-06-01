# 第16课 - 我的世界: 自拍神器

## 本课知识点回顾
* 给树莓派安装**照相机模块**
![](/assets/屏幕快照 2019-06-01 下午1.33.51.png)
* 给照相机编程有什么用？
    * 360度无死角自拍 （子弹时间）
    * 微型监控
    * 侦察车
    * 缩时摄影

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



---
![](/assets/屏幕快照 2019-06-01 下午1.34.12.png)