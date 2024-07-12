---
title: Unity—HDRP——1：Process（HDRP project setting）
data: 2024-7-12 19:52:54
updated: 2024-7-12
tags: 
    - TA
    - Process
    - Unity
    - High Definition Render Pipline
categories: Unity
description: HDRP项目初始化设置
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202407111108328.jpg
---

# 基本框架

- **Process（HDRP project setting）**
- HDRP配置文件和Volume框架
- HDRP Lighting System
- LightMapping（光照烘培）
- Material
- PostProcessing
- HDRPDebug
- HDRP Real-Time Ray Tracing

# Process（HDRP project setting）

## HDRP项目安装



窗口—>HDRP向导

![image-20240627111305585](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406271113610.png)

所有的复选框必须是绿色打勾的状态

## 项目初始化

编辑—>项目设置—>HDRP Global Setting—>默认体积配置文件资源

![image-20240627112056332](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406271120363.png)

在HDRP配置文件下面找到体积配置文件，并在此处进行修改。

项目默认使用此处的配置文件，因为我们需要自己生成项目的所有Volume配置信息，所以需要将预设全部取消。

## 使用Volume框架设置场景环境

1. 在Hierarchy窗口，新建一个空的GameObject，重命名为Scene Settings。
2. 在Inspector窗口添加一个Volume组件，然后新建一个配置文件Volume Profile，名为Scene Settings Profile。
3. 在Volume组件下面点击添加覆盖按钮，添加Visual Environment，并将类型设置为HDRI Sky，因为使用HDRI Sky提供环境光照，所以移除场景中的Directional Light。
4. 再次点击添加覆盖按钮，添加 HDRI Sky组件，然后勾选Hdri Sky 、Indensity Mode 、Exposure选项，该组件用来控制环境光强度。
5. 再次点击添加覆盖按钮，选择Shadows，使用默认的数值。
6. 尽管已经设置了HDRI和阴影的配置信息，但是需要让这些配置生效需要进一步设置，窗口—>渲染—>光照，打开光照界面在环境窗口中的配置文件，关联刚刚生成的Scene Settings Profile，并将静态光照天空改为HDRISky。
7. 在添加室内光源之前，要先为场景添加屏幕后处理效果
   1. 在Hierarchy窗口，创建一个空的GameObject。重命名为Post Processing。
   2. 为PostProcessing添加Volume组件，单击profile一栏右侧的new按钮生成PostProcessingProfile文件，用来保存后处理的更重信息。
   3. 单击添加覆盖按钮添加Exposure和Tonemapping等等。。。。
   4. 为生成的画面添加抗锯齿效果，使用Camera组件为画面添加抗锯齿效果
8. 添加光源、LightProbe 和 ReflectiongProbe。
9. 烘培光照贴图 
   1. 打开Liighting界面，确保参数设置正确![image-20240627133635025](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406271336070.png)
   2. 点击生成照明按钮开始烘培（通常不需要勾选 AutoGenerate，会导致编辑过程受到一定影响）

