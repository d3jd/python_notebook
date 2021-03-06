# 第06课-问答系统

## 本课知识点回顾

* **逻辑** 总共有三种句式
    * **if**：如果条件成立，就执行某件事
    * **if else**：如果条件成立，就执行某件事，否则执行另外一件事
    * **if elif else**：如果条件成立，就执行某件事。否则如果下一个条件成立，就执行该条件对应的事。否则执行另外一件事。
* **逻辑运算符：**在逻辑句式中把不同条件组合到一起的一种方法
    * **and（与）**：两个条件必须同时成立
    * **or（或）**：两个条件中至少成立一个
    * **not（非）**：条件不成立
* 获得用户输入的信息：使用**input()**函数
* 拼接字符串：字符串可以用 **“+”** 号拼接在一起

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

例子：如果用户输入的名字和密码都正确，欢迎用户，否则显示错误

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
![](/assets/屏幕快照 2019-07-08 上午11.52.13.png)