---
title: hexo配置
index_img: /post_index_img/hexo.jpeg
date: 
categories:
   - 工具
   - Hexo
tags:
   - 工具
   - Hexo
---


<style type="text/css">  
    body b,body strong{ color: #F07172; }
    html body img{ border-radius: 15px;box-shadow: 3px 3px 2px; }
    body .mord .cjk_fallback{ color: white; }
</style>

# 1. Mathematical formula renderer plugin

- [The plugin's repository on github](https://github.com/upupming/hexo-renderer-markdown-it-plus)

# 2. 文件保存时自动刷新浏览器

- 插件`hexo-browsersync`
- [github仓库](https://github.com/hexojs/hexo-browsersync)

# 3. 主题更新(自用)

自己的配置,请跳过

1. 下载主题包
2. 配置主题 
3. 主题原来的文件
   1. `主题\source\img`
   2. `主题\source\post_index_img`
   3.  配置`_config.yaml`

# 使用`Dark Reader`插件暗色模式`mermaid`样式修改

- 使用`Dark Reader`, `mermaid`白色的底和白色的字糊成一片
- 打开`Dark Reader`的开发者工具
- ![](hexo%E9%85%8D%E7%BD%AE/2020-04-18-15-49-55.png)
- ```css
   ================================
   lancerxxxx.github.io
   CSS
   <!-- 普通节点 -->
   .node rect, .node circle, .node ellipse,.node polygon,.node path {
      fill: #00000000 !important;
      stroke: rgb(183, 152, 248) !important;
   }
   <!-- 流程图子流程的框 -->
   .cluster rect {
      fill: #eaea5d23 !important;
   }
   <!-- 状态图节点 -->
   g.stategroup rect {
      fill: #00000000 !important;
      stroke: rgb(183, 152, 248);
   }
   <!-- 类图节点 -->
   g.classgroup rect {
      fill: #00000000 !important;
      stroke: rgb(183, 152, 248);
   }
   <!-- 甘特图 done -->
   .done0, .done1, .done2, .done3 {
      stroke: rgb(218, 214, 205);
      fill: #808080 !important;
   }
   <!-- 甘特图 active -->
   .active0, .active1, .active2, .active3 {
      fill: #6a6f8c !important;
      stroke: rgb(166, 191, 237);
   }
   ```