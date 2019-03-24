# 第09课-定位国际空间站

## 本课知识点回顾

* 国际空间站（ISS)
    * 近地轨道上最大的人造卫星。由美国和俄罗斯主导，日本，加拿大，巴西和欧洲协助完成。
* 无限循环
    * 关键词：**while True**
    * True在这里代表无条件运行，所以程序会无限循环
    * 如果写成 **while a < b** 就必须先满足 a < b 这个条件才会运行
* 字典
    * 字典是一些名字和数据的组合
    * 字典和列表的对比
        * 字典用大括号 **{}** , 列表用中括号 **[]**
        * 获取字典中的元素使用名字：somebody['名字']
        * 获取列表中的元素使用元素的位置：homework[0]
* 服务器
    * 人（和我们的个人电脑）负责向服务器提出问题（request）
    * 服务器负责回答问题 (response)
    * 人向服务器提问的方式是通过URL
* 地球坐标系：经纬度
    * **经度**：经度反映的是**东西位置**，范围在 **-180 到 180之间**
    * **纬度**：纬度反映的是**南北位置**，范围在 **90 到 -90之间**


### 无限循环
```python
while True:
    print("Big Heart!")
    print("small heart")
```

### 数据结构：字典
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
![](/assets/第09课_定位国际空间站.png)