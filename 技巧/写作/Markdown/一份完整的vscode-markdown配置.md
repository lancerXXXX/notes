---
title: 一份完整的vscode-markdown配置
index_img: /post_index_img/vscode.png
date: 2020-02-27
categories:
    - 写作
    - Markdown
tags:
    - 写作
    - Markdown
---

<head>
    <style type="text/css">  
        body b,body strong{
            background-image: -webkit-gradient(linear, left 0, right 0, from(rgb(255, 62, 242)), to(rgb(255, 0, 0)));
            -webkit-background-clip: text;
            -webkit-text-fill-color: rgba(0, 0, 0, 0);
            }
        .katex *{
            color:#1de48f;
        }
        html body img{
          border-radius: 15px;box-shadow: 12px 10px 10px;
        }
    </style>
</head>

# 1. 基础插件

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-11-42-19.png)

> All you need for Markdown (keyboard shortcuts, table of contents, auto preview and more).

# 2. 预览插件

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-11-43-09.png)

> 一个极强的markdown预览插件
> [使用文档链接](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/)

> 也可以选择 vscode 自带的markdown预览搭配预览增强的插件,但是上面这个预览插件几乎可以满足你的所有需求, 根据你的写作习惯和写作需求选择两种方式

> 自定义预览主题
> ![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-21-44.png)
> 插件本身有10来个主题可选, 用户编写的css会覆盖在选择的主题上, 所以在用户设置的css中不需要写出完整的主题,只对需要的地方更改就行

# 3. 代码片段

如果需要书写数学公式,可能更需要这部分  
先了解一下片段能带来什么  
[链接](https://bonxg.com/p/85.html)

## 3.1. vscode自带的代码块引擎

`ctrl-shift-p`

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-11-51-16.png)

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-11-51-48.png)

> 写起来较为麻烦

## 3.2. HyperSnips 第三方的代码块引擎

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-11-56-14.png)

> - 目前是预览版, 但是基本可以达到[UltiSnips](https://github.com/SirVer/ultisnips)的效果, 
>   - UltiSnips支持python, HyperSnips支持JavaScript
>     - 基于此,你可以写出很智能的片段
>     - ![box](https://github.com/draivin/hsnips/raw/master/images/welcome.gif)
>     - ![下标](https://i.loli.net/2019/05/03/5ccbc1ac18d6f.png)
>     - 在[这篇文章中](https://bonxg.com/p/85.html)的片段很多都可以使用JavaScript实现
>     - 不足的是目前不支持上下文
>   - `A`标签:
>     - UltiSnips和HyperSnips都有,自动补全:不需要按tab
>   - 单词内触发
>     - UltiSnips中使用`i`标签, HyperSnips中使用正则表达式实现,即将你的触发条件用``包住
>   - 片段规则看文档
>     - ![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-15-09.png)

# 4. 标题增加序号

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-16-19.png)

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-17-07.png)

自动增加序号

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-16-40.png)

# 5. 插入图片

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-17-44.png)

预先设置好图片的存储路径, 我设置的是 `文件名/`
可以将剪切板中的图片自动保存到设定的目录,并帮你插入到文章中

不止是图片,链接等等功能

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-18-57.png)

# 6. 表格

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-25-15.png)

表格在markdown中是较为麻烦的部分

这个插件中表格的部分我很喜欢

<center>

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-26-41.png)

![](%E4%B8%80%E4%BB%BD%E5%AE%8C%E6%95%B4%E7%9A%84vscode-markdown%E9%85%8D%E7%BD%AE/2020-02-27-12-27-09.png)

</center>

