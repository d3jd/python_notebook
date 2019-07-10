# 第08课-黑胡子的宝藏

## 本课知识点回顾

* 什么是**列表（list）**？
    * **一些**按一定**顺序排列**的数字或字符串
* 列表的例子
    * 彩票 （数字列表）
    * 作业列表 （字符串列表）
    * 购物清单 （字符串列表）
* 列表中的每一项叫做**元素**
* 列表中的元素的位置叫做**索引（index）**
* 列表可以是空的
* 向列表添加元素用 append() 函数
* 从列表删除元素用 pop() 函数
* 遍历：将列表中的元素都读出来

### 小技巧：创建列表
```python
lottery = [12, 21, 31, 45, 20]
homework = ["语文", "数学", "编程"]
empty_list = []
```

### 小技巧：读取列表中的元素
```python
homework = ["语文", "数学", "编程"]
print(homework[0])
print(homework[1])
print(homework[2])
```

### 小技巧：向列表添加元素
```python
homework = ["语文", "数学", "编程"]
homework.append("音乐")
print(homework)
```

### 小技巧：从列表删除元素
```python
homework = ["语文", "数学", "编程"]
homework.pop(1)
print(homework)
```

### 小技巧：遍历一个列表
```python
homework = ["语文", "数学", "编程"]
for i in homework:
    print(i)
```

### 高端操作：逻辑嵌套

例子：2440 < x < 2470, 750 < y < 770, x乘以y等于1889121, x和y各是多少？
```python
for x in range(2440, 2470):
    for y in range(750, 770):
        if x*y == 1889121:
            print("x is: " + str(x))
            print("y is: " + str(y))
```

---
![](/assets/屏幕快照 2019-07-10 下午4.53.13.png)