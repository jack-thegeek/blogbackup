---
title: baidu-pcs-web的曲线使用
date: 2019-08-15 23:04:37
u:
updated:
tags: 百度云
categories: 技术
---
<font color="#999999">baidu-pcs-web是个好工具</font>

<!--more-->
---
许久没用这个软件了，这个软件的牛逼之处在于，就算是限速的账号也有法子提速，详见[这篇文章](https://mp.weixin.qq.com/s?__biz=Mzg2MDA4NjU2Mg==&mid=100000023&idx=1&sn=f214af0b9f1b257b6a3222bc5d8ee303&chksm=4e2a895a795d004cd29901fa571f79cd5e0e8fe572af76c3542c4939bd31001ab1fd1a1506ef#rd)

但是今晚使用的时候一直提示file is not authorized，网盘目录也打不开。

可以搜到类似的问题，详见<https://github.com/iikira/BaiduPCS-Go/issues/460>
<img src="https://cdn.jsdelivr.net/gh/jack-thegeek/pic/2019/20190815231041.jpg">
改id是个好方法，大概是利用网盘里面的一些特殊的文件夹，让服务器误以为我们下载的不是网盘的普通文件。
直接在软件里面修改端口还是会报错的，但是我们可以参考下图操作一波，只需要把id改成266719
<img src="https://cdn.jsdelivr.net/gh/jack-thegeek/pic/2019/20190815231404.jpg">

然后就能打开根目录了