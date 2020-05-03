---
title: Virtual Box虚拟机安装
index_img: /post_index_img/
date: 2020-04-12
categories:
    - 工具
tags:
    - 工具
---

<style type="text/css">  
    body b,body strong{ color: #F07172; }
    html body img{ border-radius: 15px;box-shadow: 3px 3px 2px; }
    body .mord .cjk_fallback{ color: white; }
</style>

# 1. 和Hyper-V冲突

[参考](https://blog.csdn.net/engrossment/article/details/99431539)

- 之前装`wsl`启用了`hyper-v`, 但是装`win7`卡在`完成安装`,就想换成`Virtual Box`, 但是, 这个玩意和`hyper-v`有冲突, 会无法选择盘片(镜像)-->无法安装系统, 所以就要彻底关掉`hyper-v`
- 解决
  - `启动或关闭 Windows 功能`-->`虚拟机平台`关掉-->重启
  - `powershell`-->输入命令`bcdedit /set hypervisorlaunchtype off`

# 2. 安装

下一步, 下一步, 下一步,注意一下存储位置,

# 3. 分辨率调整

装完了屏幕比例是`4:3`,无法接受

[原文](https://blog.csdn.net/wl1070325332/article/details/78593172)

1. 打开：管理——\> 全局设定  
![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20171121153638983.png)
2. 点击扩展，点击右侧添加按钮  
![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20171121153733846.png)
3. 找到下载好的增强包，这里要注意的是增强包的后缀名要是 vbox-extpack，如果不正确将可能找不到，也不能安装成功。  
这里还要注意一点，VirtualBox 的版本要与增强包的版本一致，否则可能导致安装失败。  
![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20171121153852935.png)  
根据提示进行安装  
![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20171121153933532.png)  

至此，VirtualBox 的增强包就安装完成了。但是，年轻的你以为就这样就结束了么？

接下来，启动虚拟机，在顶部找到设备一栏。点击设备中的安装增强功能。

## 3.1. 在这里出现点安装增强功能没有反应的问题


- 下面是有反应的过程
    > 如果不出意外的话，按照默认提示一路安装就可以了。
    > 
    > 但是博主在安装过程中遇到了下面这个问题。
    > 
    > ![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/could-not-mount-the-media-drive_thumb.jpg)
    > 
    > 其实，就是因为这个媒体已经被占用了，所以不能挂载成功。。
    > 
    > 下面给出大家解决这一问题的方法：
    > 
    > 手动弹出光盘
    > 
    > ![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/right-click-cdrom-eject_thumb.png)
    > 
    >   
    > 
    > 弹出光盘之后，再次去设备中安装增强功能。(这次不成功，便成仁)
    > 
    > ![](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/device-install-guest-additions_thumb.png)
    > 
    > 
    >   
    > 
    > 由于需要超级用户权限，输入虚拟机密码后就可以成功安装啦。
    > 
    >   
    > 
    > ![](http://www.crifan.com/files/pic/uploads/2012/12/can-run-ok_thumb.png)
- 如果没有反应
  
  - [原文](https://blog.csdn.net/sjks22/article/details/80316166)
  
  - 这时候需要打开<font color=#ec4e8a>【虚拟机】</font>里的【我的电脑】,不是你机器里的
  
    这时候会多一个驱动：
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20180514221751514.png)
  
    打开，点击这个：【不是鼠标指针指着的，是那个被选中的EXE文件】
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20180514221848798.png)
  
     
  
    安装的一系列过程：
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20180514221956607.png)
  
     
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/2018051422201039.png)
  
     
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20180514222024155.png)
  
    ![img](Virtual%20Box%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%AE%89%E8%A3%85/20180514222056898.png)
  
    【注：第一个的是重启选项】
  
    重启前记得保存文件
  
    然后就ok了~
