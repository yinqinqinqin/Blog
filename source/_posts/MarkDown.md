---
title: MarkDown
data: 2024-7-8 19:52:54
updated: 2024-7-8
tags: 
    - MarkDown
    - Templatet 
categories: Comment
description: MarkDown语法模板
cover: https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202403210421347.png
---

# MarkDown

## Front Matter模板

[基于Hexo和Butterfly创建个人技术博客，(10) 使用Butterfly的Tags Plugin插件增强博客文章内容和视觉表现力_hexo+butterfly创建分类目录-CSDN博客](https://blog.csdn.net/liudonglovehemin/article/details/131095922)

```
title: 
data: 2024-03-18
tags: 
categories: 
description:
cover: 
top_img:
comments: 
keywords: 
aside: 
toc: 
swiper_index: 2


title: 文章标题
author: 作者名
data: 2024-03-18
updated: 更新日期
tags: 
		- 标签1
		- 标签2
categories: 分类
reward: 打赏（true/false）
description: 描述
cover: 封面
top_img: 顶部图片
comments: 评论（true/flase）
keywords: 关键字
aside: 侧边栏显示
toc: 文章目录
swiper_index: 优先顺序

type : 页面类型


```

## Markdown基本语法

### butterfly标签外挂

#### 行内文本

{% tabs 行内文本%}

<!-- tab 渲染效果-->

1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}

- 彩色文字
  在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
  文档「开始」页面中的标题部分就是超大号文字。
  {% span center logo large, Volantis %}
  {% span center small, A Wonderful Theme for Hexo %}

<!-- endtab -->

<!-- tab 源码示例-->

```
1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
```

<!-- endtab -->

{% endtabs %}

#### 分栏

{% tabs  分栏 %}

<!-- tab 展示效果-->

{% tabs test %}
<!-- tab 1-->
This is Tab 1
<!-- endtab -->

<!-- tab 2-->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->

{% endtabs %}

<!-- endtab -->

<!-- tab 源码-->

```
{% tabs test %}
<!-- tab 1-->
This is Tab 1
<!-- endtab -->

<!-- tab 2-->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```

<!-- endtab -->

{% endtabs %}

#### 折叠框

{% tabs 折叠框%}

<!-- tab 渲染效果-->
{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}
假装这里有代码块（代码块没法嵌套代码块）
{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}
假装这里有代码块（代码块没法嵌套代码块）
{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}
```

<!-- endtab -->

{% endtabs %}

####  提示块标签

{% tabs 提示块标签%}

<!-- tab 渲染效果-->
{% note default simple %}default 提示块标签{% endnote %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% note default simple %}default 提示块标签{% endnote %}
```

<!-- endtab -->

{% endtabs %}

{% tabs 引用%}

<!-- tab 渲染效果-->
{% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}
```

<!-- endtab -->

{% endtabs %}

#### 上标标签

{% tabs 上标标签%}

<!-- tab 渲染效果-->
{% tip success %}success{% endtip %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% tip success %}success{% endtip %}
```

<!-- endtab -->

{% endtabs %}

#### 复选列表

{% tabs 复选列表%}

<!-- tab 渲染效果-->
{% checkbox red, 支持自定义颜色 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% checkbox red, 支持自定义颜色 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
```

<!-- endtab -->
{% endtabs %}

#### 单选列表

{% tabs 单选列表%}

<!-- tab 渲染效果-->
{% radio 纯文本测试 %}
{% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% radio red, 支持自定义颜色 %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% radio 纯文本测试 %}
{% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% radio red, 支持自定义颜色 %}
```

<!-- endtab -->

{% endtabs %}

#### 记号笔注释

{% tabs 记号笔注释%}

<!-- tab 渲染效果-->
最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如CSS的{% bubble 兄弟相邻选择器,"例如 h1 + p {margin-top:50px;}" %}，{% bubble flex布局,"Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性","#ec5830" %}，{% bubble transform变换,"transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。","#1db675" %}，animation的{% bubble 贝塞尔速度曲线,"贝塞尔曲线(Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋","#de4489" %}写法，还有今天刚看到的{% bubble clip-path,"clip-path属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。","#868fd7" %}属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。
<!-- endtab -->

<!-- tab 源码示例-->

```
最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如CSS的{% bubble 兄弟相邻选择器,"例如 h1 + p {margin-top:50px;}" %}，{% bubble flex布局,"Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性","#ec5830" %}，{% bubble transform变换,"transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。","#1db675" %}，animation的{% bubble 贝塞尔速度曲线,"贝塞尔曲线(Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋","#de4489" %}写法，还有今天刚看到的{% bubble clip-path,"clip-path属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。","#868fd7" %}属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。
```

<!-- endtab -->

{% endtabs %}

#### 链接卡片

{% tabs 链接卡片%}

<!-- tab 渲染效果-->
{% link 糖果屋教程贴, https://akilar.top/posts/615e2dec/, https://cdn.cbd.int/akilar-candyassets@1.0.36/image/siteicon/favicon.ico %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% link 糖果屋教程贴, https://akilar.top/posts/615e2dec/, https://cdn.cbd.int/akilar-candyassets@1.0.36/image/siteicon/favicon.ico %}
```

<!-- endtab -->
{% endtabs %}

#### 网站卡片

{% tabs 网站卡片%}

<!-- tab 渲染效果-->

{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/avatar/avatar.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://cdn.jsdelivr.net/gh/inkss/common@master/static/web/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://cdn.jsdelivr.net/gh/MHuiG/imgbed@master/data/p.png, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}

<!-- endtab -->

<!-- tab 源码示例-->

```
{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://cdn.jsdelivr.net/gh/fomalhaut1998/cdn-assets/avatar/avatar.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://cdn.jsdelivr.net/gh/inkss/common@master/static/web/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://cdn.jsdelivr.net/gh/MHuiG/imgbed@master/data/p.png, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}
```

<!-- endtab -->

{% endtabs %}

#### 音频

{% tabs 音频%}

<!-- tab 渲染效果-->

{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}

<!-- endtab -->

<!-- tab 源码示例-->

```
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}
```

<!-- endtab -->

{% endtabs %}

#### 视频

{% tabs 视频%}

<!-- tab 渲染效果-->

{% videos %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202404170857702.mp4 %}
{% video https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/CartoonDance.mp4 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}

<!-- endtab -->

<!-- tab 源码示例-->

```
{% videos, 2 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}
```

<!-- endtab -->

{% endtabs %}

#### 相册图库

{% tabs 相册图库%}

<!-- tab 渲染效果-->

<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>


<!-- endtab -->

<!-- tab 源码示例-->

```
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
```

<!-- endtab -->

{% endtabs %}

#### 展示画廊Gallery

{% tabs 展示画廊Gallery %}

<!-- tab 渲染效果-->

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
{% endgallery %}<!-- endtab -->

<!-- tab 源码示例-->

```
{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
{% endgallery %}
```

<!-- endtab -->

{% endtabs %}

#### 按钮

{% tabs 按钮%}

<!-- tab 渲染效果-->
{% btns circle grid5 %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% endbtns %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% btns circle grid5 %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% endbtns %}
```

<!-- endtab -->

{% endtabs %}

#### 诗词标签

{% tabs 诗词标签%}

<!-- tab 渲染效果-->
{% poem 水调歌头,苏轼 %}
丙辰中秋，欢饮达旦，大醉，作此篇，兼怀子由。
明月几时有？把酒问青天。
{% endpoem %}
<!-- endtab -->

<!-- tab 源码示例-->

```
{% poem 水调歌头,苏轼 %}
丙辰中秋，欢饮达旦，大醉，作此篇，兼怀子由。
明月几时有？把酒问青天。
{% endpoem %}
```

<!-- endtab -->

{% endtabs %}

#### 时间轴样式

{% tabs 时间轴样式%}

<!-- tab 渲染效果-->

{% note blue no-icon %}

{% timeline 时间轴样式,blue %}

<!-- timeline 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
3. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

<div class="gallery-group-main">
{% galleryGroup 宗门合影 2023-10-23 '/gallery/MC/' https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202310261501300.jpg %}
</div>


{% endtimeline %}

{% endnote %}

<!-- endtab -->

<!-- tab 源码示例-->

```
{% note blue no-icon %}

{% timeline 时间轴样式,blue %}

<!-- timeline 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
3. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

<div class="gallery-group-main">
{% galleryGroup 宗门合影 2023-10-23 '/gallery/MC/' https://yin-qin.oss-cn-shanghai.aliyuncs.com/XiaoYao/202310261501300.jpg %}
</div>

{% endtimeline %}

{% endnote %}
```

<!-- endtab -->

{% endtabs %}



