# 第06课-问答系统

## 本课知识点回顾

* 为什么加密这么重要？
    * 中国古代：用虎符作为兵权的凭证
    * 苏格兰女王之死：加密不好的信泄露了秘密
    * 山本五十六的飞机被美军击落
    * 图灵破译德国恩格马机
    * 未曾被破译过的语言：印第安语，温州话
* 凯撒密码
    * 把字母表按顺序**往后移3格**, 用新的字母替换原文中旧的字母
![](/assets/alphabet.png)
* 破解凯撒密码
    * 方法1: 蛮力破解
        * 字母总共就26种，所以总共可挪动格数有26种可能
        * 测试每一种可能，找出26种结果中看得懂的那个，它就是原文
    * 方法2: 统计密文中每个字母出现的频率
        * 英文中字母e出现的频率最高
        * 密文中出现频率最高的字母对应原文字母e
        * 确定了一个字母，其它字母也就确定了，因为字母表是连续的

### 逻辑的三种句式

##### **if**：如果条件成立，就执行某件事

```python
a = 3
b = 5
if b > a:
    print("cat")
```
##### **if else**：如果条件成立，就执行某件事，否则执行另外一件事

```python
a = 3
b = 5
if b > a:
    print("cat")
else:
    print("dog")
```

##### **if elif else**：如果条件成立，就执行某件事。否则如果下一个条件成立，就执行该条件对应的事。否则执行另外一件事。

```python
a = 3
b = 5
if b > a:
    print("cat")
elif a > b:
    print("dog")
else:
    print("fox")
```


### 逻辑运算符

##### **and（与）**：两个条件必须同时成立

例子：找到一亿以内所有7和13的倍数
```python
n = 1000000000
for i in range(n):
    if i%7 == 0 and i%13 == 0:
        print(i)
```

##### **or（或）**：两个条件中至少成立一个
例子：找到一千以内小于9或大于998的数
```python
n = 1000
for i in range(n):
    if i<9 or i>998:
        print(i)
```

##### **not（非）**：条件不成立

例子：找到一千以内不是不是10的倍数的数
```python
n = 1000
for i in range(n):
    if not not i%10 == 0:
        print(i)
```


### 获得用户输入
```python
name = input('输入你的名字: ')
print('Hello ' + name + '!')

```


### 简单的密码系统

例子：计算1000万以内所有是7的倍数的数的和

```python

real_name = "皮卡丘"
real_password = "654321"

name = input('输入你的名字: ')
password = input('输入你的密码: ')

if real_name == name and real_password == password:
    print('Welcome ' + name + '!')
    print('Bingo!')
else:
    print('Wrong!')

```

---
![](/assets/第06课_问答系统.png)
