---
layout:     post
title:      Learning OpenCV
subtitle:   读书笔记
date:       2018-06-05
author:     WYB
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - OpenCV
---

# Chapter 2 介绍opencv
### Include 文件  
"opencv.hpp"包含所有文件，编译会很慢，可以单独include，查文档即可。  
### 一些资料
- A high-level overview of the whole library can be found at http://is.gd/niZvJu.
- Speedups are discussed at http://is.gd/ShvMZE.
- Modules are described at http://is.gd/izlOrM.
### 第一个程序
- ==cv::imread():==&emsp;返回cv::Mat类型  
With cv::Mat, images are automatically deallocated when they go out of scope.
- ==cv::namedWindow():==&emsp;第一个参数是窗口名，第二个参数是0(默认值)或者cv::WINDOW_AUTOSIZE
- ==cv::imshow():==
- ==cv::waitKey(0):==&emsp;0就是按下任意按键，正数就是等多少毫秒  
如果delay>0,那么超过指定时间则返回-1；如果delay=0，将没有返回值。   
或者返回值为当前键盘按键值。
### 第二个程序
用==cv::VideoCapture xxx==实例化一个读取视频的对象。然后用成员方法xxx.open()打开视频流，最后用一个Mat接收这个对象数据。
### Moving Around
就是给视频加个进度条。
### 一个小的转换程序
smoothing可以降低图片的信息量  
把图片高斯模糊一下，用cv::GaussianBlur()  
由于高斯模糊是计算中心点所以==高斯核必须是奇数==。
### 一个不是很简单的转换程序
==cv::pyrDown:==&emsp;由一个高斯平滑处理加上下采样组成。可以把图像长宽缩小一倍。  
==cv::cvtColor(input,output,cv::COLOR_BGR2GRAY):==&emsp;转换颜色  
### 从摄像头输入
==cv::VideoCapture==
### 写到AVI文件
### 练习
1.就是环境配置  
2.在lkdemo中有个追踪示例  
3.  
4.  
5.  

# Chapter 3 了解OpenCV数据类型
### 基本类型
##### the

上次看到P