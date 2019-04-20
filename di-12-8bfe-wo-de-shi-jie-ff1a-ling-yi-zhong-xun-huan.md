# 第12课 - 我的世界: 另一种循环

## 本课知识点回顾

* 任何一个编程语言中都有**两种循环**：
    * for 循环
    * while 循环
* **for循环**和**while循环**之间可以互相转换
* 在循环运行的过程中可以使用**break**关键词提前跳出循环
* Minecraft 中两个重要的函数：
    * **mc.player.getPos()** : 获得玩家在世界中的坐标
    * **mc.setBlock()** : 放置一个方块

## 例子：For 循环

```python
for i in range(1, 5):
    print(i)
```

## 例子：While 循环（形态1）：无条件循环 

```python
while True:
    print("very happy!")

```

## 例子：While 循环（形态2）：有条件循环 
```python

a = 9
b = 1
while a > b:
    print("Cat")
    print("Dog")

```

## 例子：用两种方法从0数到4
```python
# 方法1: for循环
for i in range(1, 5):
    print(i)

# 方法2: while循环
i = 0
while i < 5:
    print(i)
    i += 1
```

## 例子：让循环提前结束
```python
i = 0
while i < 5000000000:
    print(i)
    if i == 3:
        break  
    i += 1
```

## 例子：利用循环自动在脚底生成方块


```python
from mcpi.minecraft import Minecraft
import time

mc = Minecraft.create()

# 设定方块类型
block = input("Enter a block type: ")

while True:
    # 获得用户最新坐标
    pos = mc.player.getPos()
    x = pos.x
    y = pos.y
    z = pos.z

    # 将y改成用户脚下的坐标
    y -= 1

    # 在用户脚下设置方块
    mc.setBlock(x, y, z, block)
    time.sleep(0.2)

```

---
