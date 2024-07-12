---
title: Unity—HDRP——3：HDRP Lighting System
data: 2024-7-14 19:52:54
updated: 2024-7-14
tags: 
    - TA
    - Process
    - Unity
    - High Definition Render Pipline
categories: Unity
description: HDRP光照系统，烘培光照设置和流程，光照组件的介绍
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202407111108328.jpg
---

# 基本框架

- Process（HDRP project setting）
- HDRP配置文件和Volume框架
- **HDRP Lighting System**
- LightMapping（光照烘培）
- Material
- PostProcessing
- HDRPDebug
- HDRP Real-Time Ray Tracing

# HDRP Lighting System

## 目的

在HDRP中如何给场景打光

## 流程步骤

1. 场景主要分为四个部分
   - Cameras
   - Models
   - Light&Probes
   - Volumes
2. 启用Scene Settings Volume![](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406281522831.png)
3. 启用Directional Light![](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406281523050.png)
4. 启用Volume中的自动曝光控制![](https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202406281524263.png)
5. 启用所有自己设置的光源
6. 启用场景中所有的反射探针
   1. 烘培之前确保参与烘培的物体被标记为Static
7. 启用场景中的光照探针组
8. 完成整个场景的光照烘培
   - 光照贴图烘培
     1. Environment
        - 可以使用环境光Volume，前提是Volume必须包含一个sky相关的Override
     2. Mixed Lighting
        - 想要烘培全局光照，必须要勾选Baked Global Illumination
        - shadowmask和Baked Indirect区别是Shaowmask是实时的，并且消耗高
     3. Lightmapping Setting
     4. AutoGenerate（一般不建议勾选此项）
     5. Generate Lighting按钮
     6. 烘培数据展示区
   - 实时光线追踪
9. 增强间接光强度
   - 启用Scene Settings Volume
10. 处理阴影和环境光遮蔽、
    1. 只启用平行光的Shadow map选项，画面中的阴影会比较硬
    2. 设置阴影效果首先看一下AngularDiameter参数
    3. 设置接触阴影可以增加阴影细节
    4. 除了灯光投射的阴影，还可以添加MicroShadows，可以用于调整阴影的透明度
    5. 最后提娜佳Ambient Occlusion
11. 添加雾效，在Volume组件中启用Fog重载
12. 画面抗锯齿处理
13. 添加后处理Volume组件

## Night_Lighting场景打光步骤

1. 修改Directional Light设置
   1. 将平行光色温和强度调整为月光的色温和强度
2. 修改天空盒HDRI图
3. 修改曝光设置
4. 修改雾效设置
5. 修改接触阴影设置
6. ColorAdjustments颜色设置
7. 修改白平衡设置

## 光源类型和模式

1. SpotLight
2. DurectionalLight
3. PointLight
4. AreaLight
5. 自发光

### 制作和使用LightCookie为灯光添加更多细节

## 光照相关的常见问题

### 为什么场景中会出现奇怪的阴影快

### 为什么在相机镜头移动时场景中的阴影会扭曲或闪烁

### 未启用体积光的HighQuality选项，为什么编辑器中的灯光雾效会有那么多噪点

### 启用高质量选项对性能影响到底有多大

## 光源分层

### 光源分层的作用

1. 让光源只照亮场景中指定的物体，并投射阴影
2. 让光源只照亮指定的物体，但是让其他物体投射阴影

## 使用光照探针

### 为什么要使用光照探针

光照烘培可以为场景中的静态物体烘培间接光照信息，但是如何为场景中的动态物体提供间接光照信息呢？

具体作用：

1. 为静态物体提供间接光照信息
2. 为场景中那些小的物体提供间接光照信息，如果让这些小物体参与光照贴图烘培，会因为占用光照贴图空间而导致光照贴图尺寸变大，进而导致内存占用升高影响运行性能

对于小物体

1. 启用MeshRenderer组件的Contribute Global Illumination选项，让网格参与全局光烘培
2. 将ReceiveGlobalillumination（获取全局光的方式）设置为LightProbes，所以网格本身从烘培所得的间接光照信息不会被保存到光照贴图中
   1. **注意**：在烘培时，将MeshRenderer设置为从Lightmaps获取全局光照信息，待烘培完成再切换成LightProbes，此时光照探针不会起作用
3. 为场景中的移动物体提供间接光照信息

### 使用光照探针组的基本步骤

1. 创造光照探针组
2. 通过光照烘培完成间接光的生成
   1. 要想让光照探针起作用，首先需要完成对整个场景的烘培
3. 调整光照探针组
   - 如果调整了光照探针组，就需要重新烘培场景
   - 如果没有设置场景中的物体从Lightmaps获取全局光照信息，则默认情况下会使用LightProbes来获取间接光照信息
   - 光照探针摆放有一定的原则，否则容易穿帮
     - 在明暗交界的地方要多放一些光照探针
     - 因为接受光照探针间接光的物体会针对离它最近的4个探针进行采样，所以探针之间的间距要合理

### MeshRenderer组件中的Probes选项详解

如何使用MeshRenderer组件的AnchorOverride参数

## 使用ReflectionProbe为场景提供反射信息

### ScreenSpaceReflection（屏幕空间反射）

### Reflection Probe（反射探针）

## 阴影

### 阴影的种类和三种光照模式

HDRP中的阴影可以分为两类

1. 场景中光源投射的阴影
2. 基于屏幕空间信息计算的阴影