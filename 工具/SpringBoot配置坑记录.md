---
title: SpringBoot+vue配置坑记录
index_img: /post_index_img/
date: 2020-06-25 09:49:32
categories:
    - 工具
tags:
    - 工具
---


# MAVEN环境变量设置

[MAVEN配置](https://www.cnblogs.com/eagle6688/p/7838224.html)

- 解压缩到任意目录(无中文,无空格)
- 系统变量: `MAVEN_HOME`: 一直到`bin`的上一层
- 系统变量: `CLASSPATH`: 添加 `%MAVEN_HOME%\bin\`
- !!!!!!!用户变量: `CLASSPATH`: 添加 `%MAVEN_HOME%\bin\`

# Whitelable Error Page

[SpringBoot配置](https://www.cnblogs.com/miskis/p/9816135.html)

![](SpringBoot%E9%85%8D%E7%BD%AE%E5%9D%91%E8%AE%B0%E5%BD%95/2020-06-25-10-56-09.png)

![](SpringBoot%E9%85%8D%E7%BD%AE%E5%9D%91%E8%AE%B0%E5%BD%95/2020-06-25-10-56-38.png)

他这里写的是 `\test` : 照着写仍然出现报错

![](SpringBoot%E9%85%8D%E7%BD%AE%E5%9D%91%E8%AE%B0%E5%BD%95/2020-06-25-10-58-18.png)

spring官网中的例子 `\`

换成`\`之后好用了 

#### ![](SpringBoot%E9%85%8D%E7%BD%AE%E5%9D%91%E8%AE%B0%E5%BD%95/2020-06-25-10-59-08.png)


- 原因: TODO

# 安装vue-cli

[文档](https://cli.vuejs.org/zh/guide/installation.html)

注意: ![image-20200625141658920](SpringBoot%E9%85%8D%E7%BD%AE%E5%9D%91%E8%AE%B0%E5%BD%95/image-20200625141658920.png)

- 国内安装很慢, 挂梯子也慢-->用`cnpm`吧

- （1）先装一个`cnpm`，指向国内淘宝`npm`仓库。如下：

  ```
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  ```

  （2）然后再用cnpm安装vue-cli。如下：

  ```
  cnpm install -g @vue/cli
  ```