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

### 加密程序示例

##### 凯撒密码加密：输入原文（只能有小写字母和空格）和 钥匙，然后自动生成密文

```python
letters = 'abcdefghijklmnopqrstuvwxyz'

old_secret = input('Enter your secret: ')
new_secret = ''

key = input('Enter a number (1-26): ')
key = int(key)

for letter in old_secret:
    if letter == ' ':
        new_secret += letter
    else:
        old_position = letters.find(letter) # 找到字母在原字母表中的位置
        new_position = (old_position + key) % 26 # 找到字母在新字母表中的位置
        new_letter = letters[new_position] # 提取出对应的字母
        new_secret += new_letter # 将提取的字母添加到新的变量中
            
print('Your new secret is: ', new_secret)

```

---
![](/assets/第06课_问答系统.png)
