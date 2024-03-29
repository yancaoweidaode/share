# share
你可以按照以下步骤将清华源添加到 Ubuntu 20.04 的软件源中：

1. 备份原来的软件源列表，以便出现问题时可以恢复配置文件：

   ```
   sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
   ```

2. 打开软件源列表：

   ```
   sudo nano /etc/apt/sources.list
   ```

3. 在文件末尾添加清华源：

   ```
   # 清华源
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
   deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
   deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
   ```

4. 保存并退出编辑器。

5. 更新软件包索引：

   ```
   sudo apt update
   ```

现在，你可以使用清华源通过 apt 安装软件包了。


# docker的安装与使用
1. `sudo apt-get update`
2. `sudo apt-get install docker.io`
3. `docker --version` 验证是否安装成功
4. `sudo docker pull ubuntu:18.04`从dockerhub中拉取版本为18.04的ubuntu镜像
5. `sudo docker run --name my-container -d ubuntu:18.04 tail -f /dev/null` 创建一个名为“my-container”的容器并在后台运行
6. `sudo docker ps`所有正在运行的Docker容器的详细列表，包括容器ID、镜像、命令、创建时间、状态、端口等信息
7. `docker ps -a`如果您想要查看所有Docker容器的列表，包括正在运行的和停止的容器
8. `sudo docker exec -it my-container /bin/bash`
9. `docker stop my_container`关闭正在运行的容器。
10. `apt-get update && apt-get install -y sudo`新安装的容器中没有sudo命令，因此需要安装。
11. `sudo apt-get update && sudo apt-get install -y software-properties-common`新安装的容器中缺少add-apt-repository命令，因此需要安装。
12. 
```
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
```

```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
sudo apt-get update

```
```
deb https://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse

deb https://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src https://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse

```


## wsl2中使用windows的摄像头

[wsl2连接windows的外接usb设备](https://learn.microsoft.com/zh-cn/windows/wsl/connect-usb)
1. `wsl --set-default Ubuntu-20.04`设置默认的wsl2版本
2. `usbipd wsl list`在powershell中查看wsl2中的usb设备
3. `usbipd wsl attach --busid 4-3`将windows的usb设备挂载到wsl2中，`usbipd wsl detach --busid <busid>`将设备从wsl2中卸载
4. `apt-get install usbutils `在容器中安装，`lsusb`在容器中查看usb设备
5. opencv找不到设备，这是因为wsl内核没有camera驱动
![](picture/can%20not%20open%20usb_camera.png)
6. [和wsl获取usb camera有关-编译内核-1，这个帖子可以解决/dev中没有video设备的问题，其中登录windows的用户名为quzf3，至于怎么获取用户的名字，可以选择在C:\Users中查看](https://github.com/PINTO0309/wsl2_linux_kernel_usbcam_enable_conf)，这样直接获取摄像头的帧数据，速度比较慢，应该是和摄像头的分辨率有关，[参考这个帖子修改分辨率](https://zenn.dev/pinto0309/articles/e1432253d29e30)，修改相关设置之后opencv获取帧的速度变快了
8. `sudo docker run --device=/dev/video0 --device=/dev/video1 -it --user root openvino/ubuntu20_dev bash`开启一个容器，同时实现dev设备的映射
9. 修改opencv获取视频的分辨率之后，程序获取帧的速度明显加快
![使用摄像头推理所需要的时间](picture/esop/esop_camera_ms.jpg_640.png)

deb https://mirrors.ustc.edu.cn/ubuntu/ focal main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-security main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-security main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ focal-backports main restricted universe multiverse

1. [wsl启用systemd](https://zhuanlan.zhihu.com/p/569883693)
在ubuntu中使用指令`echo -e "[boot]\nsystemd=true" | sudo tee -a /etc/wsl.conf`
在windows cmd中使用'wsl --shutdown'
重新启动ubuntu
`ps --no-headers -o comm 1`判断是否启用成功，如果输出为`systemd`则成功

**先启动systemd，就可以使用**`sudo apt-get install docker.io`来之间安装docker了

sudo docker run --device=/dev/video0 --device=/dev/video1 -it --user root openvino/ubuntu20_dev bash

https://gitlab.xpaas.lenovo.com/quzf3/esop.git


```c++
#include <opencv2/opencv.hpp>
#include <ctime>
#include <iostream>
using namespace cv;
unsigned long long currentTimestamp() {
    struct timespec timestamp;
    clock_gettime(CLOCK_MONOTONIC, &timestamp);
    
    unsigned long long milliseconds = timestamp.tv_sec * 1000 + timestamp.tv_nsec / 1000000;

    return milliseconds;
}
int main()
{
    // 创建VideoCapture对象，参数为设备索引号（默认为0）
    VideoCapture cap(0);

    // 检查摄像头是否正确打开
    if (!cap.isOpened())
    {
        std::cerr << "Failed to open the camera." << std::endl;
        return -1;
    }

    Mat frame_bgr;
    while (1) {
        unsigned long long start = currentTimestamp();
        cap >> frame_bgr;
        unsigned long long end = currentTimestamp();
        std::cout << "time of get a frame is " << end - start << std::endl;
    }

    imwrite("./out.jpg", frame_bgr);

    // 进行视频捕获和处理的代码...

    return 0;
}
```
```
cmake_minimum_required(VERSION 3.0)
project(opencv_usb_camera)

set(CMAKE_CXX_STANDARD 11)

# 查找OpenCV库
find_package(OpenCV REQUIRED)

# 添加可执行文件
add_executable(capture capture.cpp)

# 链接OpenCV库
target_link_libraries(capture ${OpenCV_LIBS})
```
`apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio`