---
title: Unity—HDRP——2：HDRP配置文件和Volume框架
data: 2024-7-13 19:52:54
updated: 2024-7-13
tags: 
    - TA
    - Process
    - Unity
    - High Definition Render Pipline
categories: Unity
description: HDRP高清渲染管线的配置文件和Volume框架介绍
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202407111108328.jpg
---

# 基本框架

- Process（HDRP project setting）
- **HDRP配置文件和Volume框架**
- HDRP Lighting System
- LightMapping（光照烘培）
- Material
- PostProcessing
- HDRPDebug
- HDRP Real-Time Ray Tracing

# HDRP配置文件和Volume框架

## 介绍

主要作用就是用来管理HDRP的所有渲染功能，首先会使用HDRP的配置文件生成一个HDRP的渲染管线实例，而这个渲染管线的实例则包含用于渲染的中间资源。

## FrameSettings（帧设置）

帧设置主要针对场景中的Camera、Baked or Custom Reflection和Realtime Reflection的相关设置。

帧设置的优先级低于HDRP配置文件，即HDRP文件中没有打开某项功能，那么帧设置中对应的功能会被自动禁用。默认帧设置参数如下![image-20240627134815573](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406271653876.png)

可在下拉选项中进行设置

## Volume框架

Volume的作用是通过调整各项HDRP参数，影响相机所看到的画面的最终渲染效果。

Volume的优先级低于帧设置，即假如在当前相机的帧设置中没有打开某项功能，那么在Volume中对相关功能的调整是不起作用的。

### Rendering（渲染）

#### 1.Color Buffer Format（颜色缓存格式）

出于性能考虑，HDRP默认使用R11G11B10格式（不含Alpha通道）

如果要把HDRP渲染的画面合成到另外的图片上，就需要包含Alpha通道，这时就要选择R16G16B16A16

#### 2.Lit Shader Mode（Lit着色器模式）

- Forward
- Deferred
- Both
  - 选择Both会让HDRP编译其他两种渲染方式着色器的变体

选择Forward或Both模式，可以选择MSAA抗锯齿效果

#### 3.Motion Vectors（运动矢量）

HDRP可以在屏幕空间反射和运动模糊中使用运动矢量，通过Camera组件启用的TAA必须使用运动矢量才能正常工作。

#### 4.Runtime Debug Display（运行时Debug显示）

可以在运行时显示灯光和材质的属性信息，会增加构建时间和着色器内存占用

#### 5.Dithering Cross-fade （平滑转换）

HDRP在做LOD转换时进行平滑的转换

#### 6.Terraub Hole（地形洞）

启动后可以显示地形上的凹陷孔洞

#### 7.Transparent Backface（透明背面）

如果场景中没有使用透明材质或者不会渲染透明材质的背面。则可以禁用来减少构建时间

此功能与Lit材质中的BackThenFrontRendering相关联，启用透明背面之后，材质中的这个选项才会有效果

#### 8.Transparent Depth Prepass（透明深度预处理）

如果你的场景中没有使用透明材质，禁用此选项减少构建时间。

#### 9.Transparent Depth Postpass（透明深度后处理）

如果你的场景中没有使用透明材质，禁用此选项减少构建时间。

#### 10.Custom Pass（自定义通道）

如果没有使用Custom Pass功能，则禁用此功能可以节约内存

#### 11.Realtime Raytracing（实时光线追踪）

如果要在HDRP中使用实时光纤追踪功能，则要先启动此选项

#### 12.LOD Bias（LOD偏差）

场景中的相机会使用此数值来计算LOD偏差

#### 13.Maximum LOD Level（最大LOD级别）

用于设置相机支持的最大LOD级别

#### 14.Decals（贴花）

调整与贴花相关的设置

- Draw Distance（渲染距离）
- Atlas Width和Atlas Height
- Metal and Ambient Occlusion Properties
- Maximum Clustered Decals on Screen

#### 15.Dynamic Resolution（动态分辨率）

#### 16.Low res Transparency（低分辨率透明）

### Lighting（光照）

### Lighting Quality Settings（光照质量设置）

### Material（材质）

### Post-Processing（后处理）

### Post-processing Quality Setting（后处理质量设置）

## 针对不同平台使用不同的HDRP配置

# Volume框架详解

## 作用

- 为场景设置来自天空盒的光照
- 设置各种阴影效果
- 设置场景中的雾效
- 设置基于屏幕空间的反射和折射
- 设置后处理效果
- 设置实时光线追踪

## 使用方法

1. 创建一个空的GameObject，然后添加Volume组件，并添加各种所需的重载（override）
2. Global模式和Local模式
   1. Global模式是全局生效
   2. Local模式是碰撞范围内生效
3. 要让Volume组件生效，需要将参数保存到一个配置文件中来

## 参数类别

一共分为九个参数

