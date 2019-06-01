# 第16课 - 我的世界: 自拍神器

## 本课知识点回顾
* 给树莓派安装**照相机模块**
![](/assets/屏幕快照 2019-06-01 下午1.33.51.png)
* 给照相机编程有什么用？
    * 360度无死角自拍 （子弹时间）
    * 微型监控
    * 侦察车
    * 缩时摄影

## 例子：启动摄像头
用程序开启摄像头，5秒后自动关闭
```python
from picamera import PiCamera  # 导入照相机模块
import time

camera = PiCamera()  # 与照相机建立连接

camera.start_preview()  # 启动照相机

time.sleep(5)  # 暂停 5秒

camera.stop_preview()  # 关闭照相机

```

## 例子：拍照
用程序开启摄像头，5秒后拍一张照片，然后自动关闭摄像头
![](/assets/屏幕快照 2019-06-01 下午1.42.06.png)
```python
from picamera import PiCamera  # 导入照相机模块
import time

camera = PiCamera()  # 与照相机建立连接

camera.start_preview()  # 启动照相机

time.sleep(5)  # 暂停 5秒

camera.capture('/home/pi/Desktop/image.jpg')  # 拍照

camera.stop_preview()  # 关闭照相机


```

## 例子：连环拍照
每隔3秒拍一张照片，拍完5张照片后结束拍照
![](/assets/屏幕快照 2019-06-01 下午1.43.27.png)
```python
from picamera import PiCamera # 导入照相机模块
import time

camera = PiCamera()  # 与照相机建立连接

camera.start_preview()  # 启动照相机

time.sleep(5)  # 暂停 5秒

for i in range(5):
    time.sleep(3)
    camera.capture('/home/pi/Desktop/image' + str(i) + '.jpg')


camera.stop_preview() # 关闭照相机

```

## 例子：视频录制程序
录制一个短视频

第1步：写视频录制程序并运行
```python
from picamera import PiCamera  # 导入照相机模块
import time

camera = PiCamera()  # 与照相机建立连接
camera.resolution = (640, 360)  # 将照片分辨率变小

camera.start_preview()  # 启动照相机

camera.start_recording('/home/pi/video.h264')  # 开始录制视频
time.sleep(10)  # 等待10秒
camera.stop_recording()  # 结束录制视频
camera.stop_preview()  # 关闭照相机
```
第2步：用CLI将录制好的视频转换成mp4格式
sudo apt-get install gpac
MP4Box -add video.h264 something.mp4


---
![](/assets/屏幕快照 2019-06-01 下午1.34.12.png)