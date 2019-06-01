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



---
![](/assets/屏幕快照 2019-06-01 下午1.34.12.png)