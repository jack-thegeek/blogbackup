---
title: Font Awesome
date: 2019-08-18 23:10:58
u: true
updated:
tags: Hexo
categories: 技术
---
<font color="#999999">日志详情：了不起的图标字体</font>

<!--more-->
---
# Font Awesome
一直想更换放在首页的几个很模糊的社交图标，刚好前不久接触到图标字体的概念，终于有时间下手了。
字体图标，又或者叫图标字体，怎么称呼不重要，重要的是它以字体的格式存在，但是输出的又是图标，很佩服想出这种字体的那些人，这个想法本身就很awesome
优点非常明显，引用[CSDN](https://blog.csdn.net/weixin_41399785/article/details/79800043)中的一段
>轻量级：一个图标字体要比一系列的图像要小。一旦字体加载了，图标就会马上渲染出来，不需要下载一个个图像。这样可以减少HTTP的请求数量，而且和HTML5的离线存储配合，可以对性能做出优化。

>灵活性：不调字体可以像页面中的文字一样，通过font-size属性来对其进行大小的设置，而且还可以添加各种文字效果，如color、hover、filter、text-shadow、transform等效果。灵活的简直不像话！

>兼容性：图标字体支持现代浏览器，甚至是低版本的IE浏览器，所以可以放心的使用它。

>相比于位图放大图片会出现失真、缩小又会浪费掉像素点，图标字体不会出现这种情况。

至于劣势，基本是颜色渲染较为单一、版权问题，如果要自己制作维护的话比较花时间。

就我目前的知识来说，除了SVG格式的矢量图，没有能跟它匹敌的图标方案，况且博客本身有些地方就引入了Font Awesome，所以愉快地敲定方案。

# 困难
入门非常简单，引入css，就可以直接使用了。
使用教程参考[中文文档案例](http://www.fontawesome.com.cn/examples/)
最方便的当然是通过CND引入，推荐使用<https://www.bootcdn.cn/font-awesome/>
官网：<https://fontawesome.com/>
已经很久没更新的中文官网：<http://www.fontawesome.com.cn/>

问题我用的是Hexo框架，加上大量精简过的[yelee](https://github.com/MOxFIVE/hexo-theme-yelee)，所以要修改多个文件。

# 过程
## 1.引入css文件
在\layout\_partial\head.ejs中head标签的最后加入
```html
<link href="https://cdn.bootcss.com/font-awesome/5.10.0-12/css/all.css" rel="stylesheet">
```

## 2.left-col.ejs与mobile-nav.ejs
在开发者工具中可以看到，负责社交图标的类名为social，直接用sublime text3搜索整个主题文件夹，可以得到三个结果，其中两个ejs文件就是要修改的模板。
打开layout\_partial\left-col.ejs，可以看到
```cs
<% for (var i in theme.subnav){ %>
	<a class="<%= i %>" target="_blank" href="<%- url_for(theme.subnav[i]) %>" title="<%= i %>"><%= i %></a>
<%}%>
```
这里很巧妙，仅仅用了一个for循环来从主题_config.yml中的subnav部分读取社交图标的名称，传递到输出中，依葫芦画瓢，修改后的代码如下：
```cs
<% for (var i in theme.subnav){ %>
	<a target="_blank" href="<%- url_for(theme.subnav[i]) %>" title="<%= i %>">
		<i class="<%= i %>" aria-hidden="true" style="font-size: 23px;"></i>
	</a>
<%}%>
```
mobile-nav.ejs的修改是一模一样的

## 3.\_config.yml
上述操作主要是把id字段传到i标签中，要遵循font awesome的规范，所以_config.yml中要把对应的社交图标名称更改为
```
fab fa-github: "https://github.com/jack-thegeek/jack-thegeek.github.io"
fab fa-weixin: ""
```
一时间我也没去深究为什么有fa，fas，fab几种，具体名称参照<https://fontawesome.com/icons?d=gallery&m=free>,点开一个图标就可以看到它的插入代码，非常方便。~~就是网站有点慢~~

## 4.main.styl
上述步骤完成后，发现压根看不到图标，开发者工具中是可以看到元素已经放进去的了，但就是看不见，差点怀疑人生。
冷静下来想想，只有可能是样式控制那里出问题了。
打开\source\css\_partial\main.styl,搜索social可以看到这样一段
```
a {
	border-radius:50%;
	display:-moz-inline-stack;
	display:inline-block;
	vertical-align:middle;
	*vertical-align:auto;
	zoom:1;
	*display:inline;
	text-indent:-9999px;
	margin:0 8px 15px 8px;
	opacity:0.8;
	width:28px;
	height:28px;
	transition:0.3s;
	&:hover {
		opacity:1
	}
```

有一行代码吸引了我
`text-indent:-9999px;`
这是个神奇的操作，作用可以参考<https://blog.csdn.net/bulabulahei/article/details/89045210>
但在这里我们不需要，所以删掉它即可

看圆角就知道，本来的方案是，画一个圆形，填上不同的颜色，然后在圆形里面放上透明的图标
而后下面带社交图标名称的样式可以全部删掉
改成我们需要的
```
i.fa-github{color: #47484c;}
```
由于大小已经直接在第2步中统一控制了，这里只需要控制颜色。
至此，把所有样式补充完整，大功告成。


# 最后
Font Awesome是个好东西，到现在已经发展到第5个大版本，免费的图标多达1500+
修改模板遇到非常多的坑，但是这样一来，对模板的结构又有了更深层的了解，对后面打算重构移动页面侧边栏很有帮助。