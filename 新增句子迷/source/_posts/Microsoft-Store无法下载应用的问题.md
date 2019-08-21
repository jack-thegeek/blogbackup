---
title: 微软商店无法下载应用的问题
date: 2019-08-14 08:25:54
u: true
updated:
tags: Windows
categories: 技术
---
<font color="#999999">解决Microsoft Store不能下载的问题</font>

<!--more-->
---
这是个老问题，也是个疑难杂症。遇到过很多次，无论是自己电脑还是别人的，可以尝试的方法无非以下几个：

1. 更换114的DNS
也可以尝试谷歌的或者其他的国外DNS,但我觉得114上store是最稳的，用完最好换回国内的，关于DNS的问题以后会有文章专门介绍。
如果这能解决问题，这是最轻松的。

2. 删除store缓存之一
官方的解决方案：用[WSReset.exe](https://answers.microsoft.com/zh-hans/windows/forum/windows_10-windows_store/microsoft-store/17b4e317-46ff-4c4f-91cb-0d08f880a593?auth=1)

>按“Win+R”键，在运行窗口中，键入` WSReset.exe`并点击“ 运行 ”。
>如果问题依旧，建议您尝试以下方案重新部署您的应用商店：
>在打开的“管理员：Windows Powershell”窗口中输入以下命令：
>`get-appxpackage *store* | remove-Appxpackage`
>再次安装：
>`add-appxpackage -register "C:\Program Files\WindowsApps\*Store*\AppxManifest.xml" -disabledevelopmentmode`

3. 删除store缓存之二
参考IT之家的教程：[Win10商店还不能下载应用？试试这四种方法](https://www.ithome.com/html/win10/169732.htm)
重新登录微软帐号值得一试，~~通常没什么用~~

>打开服务，关闭windows update
>打开服务的方法很多，最方便的应该是win+q弹出搜索，直接搜服务，如下图
<img src="https://cdn.jsdelivr.net/gh/jack-thegeek/pic/2019/20190814094648.jpg">
>然后找到windows update，把它关了
>删除C:\Windows\SoftwareDistribution
>重新开启windows update
>重启一下

3. 重置网络
昨天给家里的台式重装了个[精简过的系统](https://www.winos.me/archives/1352.html)，之前一直认为，去MSDN下载官方的镜像最纯净，自然就很抵触这些修改过的系统。
<br/>现在想法又变了，看到4G多的系统精简到1.6G，释放完之后占用不到10G的硬盘（原版的安装完大概30G+），这是有水平的精简，况且目前用下来，并没有什么大问题。
<br/>4G内存跑这个系统也没啥问题，就是精简得有点过了，计算器没了得把它下载回来。上述方法都无效果，每次都是下载到一半然后失败。这时我想，能下载到一点那应该不是网络的问题了，所以一直在缓存上下手。突然看到一条评论，重置网络就好了，不抱希望地在命令行中敲入`netsh winsock reset`，重启，然后就可以下载了。

到最后也不知是不是这句命令的功劳，这些疑难杂症就是这样，每次都是些不抱希望的操作，居然就好了，几经折腾也不懂最后到底是怎么解决的，重置网络作为一个参考吧。
删除文件夹跟重置网络都是“重药”，用了之后可能会有其他新的奇奇怪怪的问题，不是不能用，是不到最后还是别用的好，毕竟Windows的事情，谁说得准呢？