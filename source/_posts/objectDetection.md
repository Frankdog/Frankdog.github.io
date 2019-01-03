---
title: object detection
date: 2018-04-25 15:59:28
tags: cnn
categories: deep learning 
---
- [R-CNN](#r-cnn)
  - [fine-tune CNN网络](#fine-tune-cnn网络)
  - [训练 SVM 分类器](#训练-svm-分类器)
  - [合在一起](#合在一起)

<!-- more -->

# R-CNN
## fine-tune CNN网络  
+ fine-tune alexnet  
    - 修改alexnet proto 全连接层输出个数(N+1)[分类个数]  
    - 使用selective search 对图像生成region proposal  
    - 根据regional proposal 与  ground truth的IOU > 0.5 正样本，其他为负样本  
    - fine-tune alexnet  


## 训练 SVM 分类器  



## 合在一起
+ selective search 产生region proposal
+ region proposal 使用 fine-tune CNN 网络提取特征
+ 使用 每一类SVM 分类器 判断是否属于该类
