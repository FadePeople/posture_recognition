# 1. Overview ![pic](https://camo.githubusercontent.com/2d21dcc74fc13272cce1a3b020085968fc269cf7/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f70726f70657274792d706572736f6e616c2532307265706f7369746f72792d627269676874677265656e2e737667)



- ![pic](https://img.shields.io/badge/Author-%40wfnian%F0%9F%98%81-red.svg)
- 基于普通摄像头的太极姿势识别(分类)，通过openpose采集的骨骼点数据做分类。
  - 第一就是通过openpose采集的骨骼数据做一个自定义特征的全连接网络的训练分类。（已完成）
  - 第二就是通过openpose采集的骨骼图片做卷积神经网络（CNN）分类（已完成）
- 相关：[基于Kinect的姿态识别(分类)](https://github.com/wfnian/kinect/wiki)
- 若有需要和问题可提issues.

## 1.1. 安装与使用

首先根据OpenPose WindowsAPI安装说明安装，调用方式为Python调用。  
[OpenPose GitHub地址](https://github.com/CMU-Perceptual-Computing-Lab/openpose)  
<u>[OpenPose安装说明](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/installation.md)</u>
最近迁移至Ubuntu，Windows的更新后cuda与caffee不兼容。部分程序有改动。总体不变。

### 1.1.1. 程序开发目录说明

> `git clone` 下来后`cmake`进行编译,其中要勾选`BUILD_PYTHON`进行编译才能被python调用。

workspace 程序开发目录详细说明

- 📂workspace
  - 📁data_collection(数据采集)
    - data_collection_window.py
    - data_collection_window.ui
    - data_collection.py
  - 📁dataset (数据集)
    - 📁taichi
      - 📁marked_pic
        - 🎴 p_2_0.jpg（最后一个下划线后面是类别，此处`0`是类别，前一个数字`2`代表大概数量）
        - 🎴 ...
      - 📄bone_dataSet.data(骨骼特征数据)
      - 📄marked_pictrain.txt(图片路径)
  - 📁main_program
    - main.py 主程序入口
    - mainWindow.py
    - mainWindow.ui
  - 📁model_pth (模型保存位置)
    - 23classification_eigenvalue.pth
    - 23classification_pic.pth
  - 📁neural_network
    - 📁runs (tensorboard 可视化,如果有必要)
    - 📃classification23_taichi_eigenvalue.py
    - 📃classification23_taichi_pic.py
    - 📃data_process.py
    - 📃predict_eigenvalue.py
    - 📃predict_pic.py
  - 📁openpose_python_demos (包含一些python使用openpose的例子)
    - 📃flags.hpp(调用openpose的参数设置)
    - 📃use_camera_by_opencv.py
    - 📃use_camera.py
  - 📁sundry (包含一些界面设计的图片等杂项)
    - ...

## 1.2. 训练效果

| 全连接 | 卷积网络 |
| :-: | :-: |
| ![pic](workspace/sundry/train_loss_acc_eigenvalue.png)    | ![pic](workspace/sundry/train_loss_acc_pic.png)       |

## 1.3. 展示效果

| 数据采集系统 | 识别系统 |
| :-: | :-: |
| ![pic](workspace/sundry/res2.gif)    | ![pic](workspace/sundry/res1.gif)|



## 1.4. 答辩结果

> 校级答辩 `优秀` 哈哈哈哈哈
