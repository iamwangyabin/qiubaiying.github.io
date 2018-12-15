---
layout:     post
title:      深度学习框架PyTorch入门与实践
subtitle:   读书笔记
date:       2018-06-05
author:     WYB
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - PyTorch
---

# 简介

# 快速入门

# Tensor和autograd

## 3.1 Tensor
接口分：

(1)torch.function

(2)tensor.function

大部分操作都同时支持这两种操作，如torch.sum(a,b)==a.sum(b)

存储角度分：

(1)不会修改自身

(2)会修改自身操作--以_结尾的function

一些函数……
## 3.2 autograd

# 神经网络工具箱nn

# PyTorch中常用工具




# GAN
对抗网络  
其实Descrimater能产生图片，但是不适合产生图片，因为1、不擅长生成2、D擅长批评，如果只用正面例子训练则训练出来所有东西都会认为是高分，需要有负面例子，没有很多好的负面例子，有可能学到错误的地方。因为我们不知到怎么获得好的负例子所以……