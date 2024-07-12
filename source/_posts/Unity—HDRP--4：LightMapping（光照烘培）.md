---
title: Unity—HDRP——4：LightMapping（光照烘培）
data: 2024-7-15 19:52:54
updated: 2024-7-15
tags: 
    - TA
    - Process
    - Unity
    - High Definition Render Pipline
categories: Unity
description: HDRP光照贴图原理介绍
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/img/202407111108328.jpg
---

# 基本框架

- Process（HDRP project setting）
- HDRP配置文件和Volume框架
- HDRP Lighting System
- **LightMapping（光照烘培）**
- Material
- PostProcessing
- HDRPDebug
- HDRP Real-Time Ray Tracing

## 摘要

- 什么是光照烘培?
- 什么是光照贴图？
- 为什么要用光照贴图？

## 渐进式光照贴图烘培对场景中的模型有什么要求？

1. 模型上不能有重叠的UV
2. UV之间要有足够的间距以避免渗色现象的发生
3. 因为使用光照贴图只能烘培静态物体，所以要把需要参与烘培的物体标记为Static

## 进行渐进式光照贴图烘培时烘培出来的是什么？

烘培出来的时光照贴图，光照探针和反射探针

按照不同的LightingMode光照模式，烘培出来的结果是不同的，光照贴图中会包含 间接光照信息，也会包含软阴影和环境光遮蔽的信息。

可以选择两种光照模式

1. BakedIndirect模式
   1. 如果将场景中的光源设置为Mixed那么这些灯光会给场景提供直接光照，简介光照会被烘培到光照贴图和光照探针中，此模式下，会投射实时阴影
2. Shadowmask模式
   1. 与BakedIndirect区别是，能在运行时，将烘培所得到的阴影和实时阴影进行融合，可以获得最高质量的阴影，同时对性能和内存的要求也是最高的

## 光照贴图烘培界面参数详解

## 如何解决光照贴图接缝问题

由于GPU无法在分开的光照贴图之间混合纹理

启用MeshRenderer组件中的StitchSeams选项，勾选会增加烘培时间
