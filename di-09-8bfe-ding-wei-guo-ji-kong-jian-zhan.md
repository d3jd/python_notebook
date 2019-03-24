# 第09课-定位国际空间站

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

### 小技巧：无限循环
```python
while True:
    print("Big Heart!")
    print("small heart")
```

### 小技巧：数据结构：字典
```python
# 个人档案
somebody = { "名字": "李好", "年龄": 104, "爱好": "唱歌"}

print(somebody['名字'])
print(somebody['年龄'])
print(somebody['爱好'])

# 游戏人物
pikachu = {"名字": "皮卡丘", "等级": 45, "职业": "剑客", "经验值": "1023"}

print(pikachu['名字'])
print(pikachu['等级'])
print(pikachu['职业'])
print(pikachu['经验值'])
```


### 例子：空间站中都有谁？
```python
import requests

# 通过API获得数据
url = 'http://api.open-notify.org/astros.json'
response = requests.get(url)
result = response.json()

# 获得空间站的总人数
total_people = result['number']
print('国际空间站中总共有: ' + total_people + '人')

# 获得空间站中的每个人
people = result['people']
for p in people:
    name = p['name']
    print(name + '在空间站里！')

```

### 例子：获得空间站的经纬度
```python
import requests
import time

# 无限循环
while True:

    # 通过API获得数据
    url = 'http://api.open-notify.org/iss-now.json'
    response = requests.get(url)
    result = response.json()

    # 获得空间站的经纬度
    location = result['iss_position']
    lat = location['latitude'] #纬度
    lon = location['longitude'] #经度

    # 打印出空间站的经纬度
    print('纬度是: ', lat)
    print('经度是: ', lon)

    # 减慢获得数据的频率
    time.sleep(1)
```

### 例子：实时跟踪国际空间站
注意：**iss_02.gif** 和 **map.gif** 必须和代码在同一文件夹中

![](/assets/iss_02.gif)
![](/assets/map.gif)
![](/assets/tracking_satellite.png)
```python
import requests
import turtle
import time

# 创建屏幕
screen = turtle.Screen()
screen.setup(1024, 512)
screen.bgpic('map.gif')
screen.register_shape('iss_02.gif')
screen.setworldcoordinates(-180, -90, 180, 90)

# 将turtle的样子设置为空间站
iss = turtle.Turtle()
iss.shape('iss_02.gif')
iss.setheading(90)
iss.penup()

while True:
    url = 'http://api.open-notify.org/iss-now.json'
    response = requests.get(url)
    result = response.json()

    location = result['iss_position']
    lat = location['latitude']
    lon = location['longitude']
    print('Latitude: ', lat)
    print('Longitude: ', lon)

    iss.goto(float(lon), float(lat))
    time.sleep(1)

```



---
![](/assets/幻灯片58.png)