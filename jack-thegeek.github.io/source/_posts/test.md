---
title: test
date: 2019-07-31 11:21:18
tags: 技术
categories: 技术
---
# pic testing
<div align="center">
    <img src="https://pic1.superbed.cn/item/5d411cad451253d178ecb6c6.jpg" alt="加载不出图片显示字样" title="鼠标悬停显示字样" width="25%">
</div>

<!--more-->

# text testing
<div style="color: #248ea9">
    <br/>看样子是可以直接在md中写html的代码，不清楚他怎么渲染的。<br/>
    顺便换了个颜色<br/>
</div>

# 如果要给标题换颜色

<div style="color: yellow">
    # 标题实例
</div>

代码如下
```
# pic testing
<div align="center">
    <img src="https://pic.superbed.cn/item/5cd384873a213b04170f8e74.jpg" alt="加载不出图片显示字样" title="鼠标悬停显示字样" width="25%">
</div>

# text testing

<div style="color: #248ea9">
    <br/>看样子是可以直接在md中写html的代码，不清楚他怎么渲染的。<br/>
    顺便换了个颜色<br/>
</div>

<div style="color: yellow">
    # 标题实例
</div>

```

<br>想插入个音乐来着，结果
<div align="center">
    <img src="https://pic.superbed.cn/item/5d411148451253d178ec37d6.jpg" width="50%">
</div>

***

<br/>那咱来首没有版权问题的<br/>

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=493911&noauto=1&height=66"></iframe>

然后再回到有版权那首（获取音频这波操作就先隐去了）<br/>
<audio controls>
  <source src="/audio/Rain-after-summer.mp3" type="audio/mpeg">
您的浏览器不支持 audio 元素。
</audio>

这里用了html5的标签，然后是本地的文件，github只有1g空间，所以尽量少用
**然后发现个尴尬的事情，13m的文件传上github真是为难我27k/s的网络，所以最终放弃了**
至于界面，自然没有网易云的控件那么好看，估计网上也有教程，以后再研究，代码长这样
```
<audio controls>
  <source src="/audio/Rain-after-summer.mp3" type="audio/mpeg">
您的浏览器不支持 audio 元素。
</audio>
```
