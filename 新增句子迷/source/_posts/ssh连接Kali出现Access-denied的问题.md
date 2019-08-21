---
title: ssh连接Kali出现Access denied的问题
date: 2019-08-06 18:02:06
tags: linux
categories: 技术
---
<font color="#999999">关于ssh连接Kali Linux时出现Access denied的解决方法</font>
<style type="text/css">
	img{
		max-width: 90%;
	}
</style>

<!--more-->
---

网上的方法大同小异，无非是以root账户，修改ssh_config或者sshd_config,问题就出在这，网上的方法大多只有其中一个文件，参考了几个教程后才发现这是两个不同的文件。

所以要分别更改不同的配置(黄色为更改部分)：
```text
root@kali:/etc/ssh# vi ssh_config 
```
<img src="https://ae01.alicdn.com/kf/Hdfcc5d93c1444305a64ab7cfa50a6f6cd.jpg">
```
root@kali:/etc/ssh# vi sshd_config 
```
<img src="https://ae01.alicdn.com/kf/Hc5a8835754b7431c99761666f3b5eb328.png">

开启ssh服务
```
/etc/init.d/ssh start
```
查看ssh状态
```
/etc/init.d/ssh status
```
设置开机启动
```
update-rc.d ssh enable
```

然后就可以用putty连上去了啦