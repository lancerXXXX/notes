---
title: Windows/Linux软链接
index_img: /post_index_img/技巧.png
date: 2020-04-02
categories:
    - 技巧
    - Windows
tags:
    - 技巧
    - Windows
---

<style type="text/css">  
    body b,body strong{ color: #F07172; }
    .katex *{ color: #139f64; }
    html body img{ border-radius: 15px;box-shadow: 6px 7px 4px; }
    body .mord .cjk_fallback{ color: white; }
</style>

[原文](https://www.cnblogs.com/lsdb/p/6667555.html)

1.Wondows 创建软链接和硬链接
-------------------

`mklink [/d] [/h] link target`
`mklink [/d] [/h] 要把链接文件放的路径 被链接的文件路径`

`/d`-- 创建目录软链接；默认为文件软链接；创建目录链接时必须使用该选项不然创出的软链接无效  
`/h`-- 创建硬链接；默认为软链接  
`link`-- 指定新的符号链接名称（相对或绝对）  
`target`-- 指定新链接引用的路径（相对或绝对）

说明：如果创建软链接提示 “你没有足够的权限执行此操作”，那改以管理员身份启动 CMD 再重新执行创建命令。

![](simpread-Windows%20%E5%92%8C%20Linux%20%E5%88%9B%E5%BB%BA%E8%BD%AF%E9%93%BE%E6%8E%A5%E5%92%8C%E7%A1%AC%E9%93%BE%E6%8E%A5/2020-04-02-11-45-17.png)


> 示例：
> ```node.js
> mklink /d c:\Users\ls\Desktop\books f:\books
> ```

2.Linux 创建软链接和硬链接
-----------------

`ln [-s]  target link`


`-d--` 尝试对目录进行硬链接时用，一般会失败；创建软链接时文件和目录都一样建，不用 `- d`

`-s--` 创建软链接；默认创建硬链接

`target/link--Linux` 与 `Windows` 顺序相反

软链接（即符号链接）和硬连接的异同

同：对 Link 或 Target 修改全部文件都会修改

异：删除软链接对源文件无影响删除源文件软链接不能访问；删除硬链接或源对对方都没有影响；硬链接只能在同一磁盘（即文件系统）下；硬链接不能对目录创建