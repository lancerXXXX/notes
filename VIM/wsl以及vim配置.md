---
title: wsl以及vim的配置
date: 2019-8-15
categories:

  - wsl
  - vim

tags:

  - wsl
  - vim

---

# 提示

`过程中如果出现了问题 第一步 切换root和非root即sudo su和exit   重试 如果不行   ` 
`第二步  关掉终端重新开 重试 如果不行` 
`第三步 百度,必应,google.....重试 如果不行` 
`第四步 关机重启 如果不行` 
`第五步 卸载Ubuntu  先看C:\Users\用户名\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc\LocalState\rootfs这里的东西删没删掉 ` 
`如果删掉了就重装` 
`如果删不掉 新建txt ` 

``` 
DEL /F /A /Q \\?\%1
RD /S /Q \\?\%1
```

`写进上边,后缀改成.bat  把文件夹托上去删掉` 

## 更新的部分在这里

markdown 预览插件我换成了这个[
这个](https://github.com/suan/vim-instant-markdown)
具体设置看官方文档

# 解决访问GitHub太慢

需要访问GitHub 所以要先解决这个问题
https://blog.csdn.net/weixin_38437404/article/details/89489401

# 安装Ubuntu

1. 打开适用于Linux的Windows子系统

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811121024967.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

2. 重启电脑之后

Microsoft Store安装Ubuntu

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811121243692.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

3. 安装ing

输入用户名 密码

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811121411572.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811122337315.png)

点Ubuntu图标-->属性

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811122428473.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

Ctrl shift C/V那个开  

4. 换中科大源(目前别的源后面过程有坑,别问我怎么知道)

	

``` 
	##中科大源

	deb https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
	deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic main restricted universe multiverse
	deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
	deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
	deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
	deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
	deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
	deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
	deb https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
	deb-src https://mirrors.ustc.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
	```

备份原来的

``` 
sudo cp /etc/apt/sources.list /etc/apt/sources_init.list
sudo vim /etc/apt/sources.list
```

如果没用过vim

* 原来的都删掉

``` 
 100dd
```

* 复制上边的源, 然后

``` 
i
Ctrl Shift V
```

* 换普通模式

`Esc` 

* 保存退出

``` 
:wq
```

然后输入命令

``` 
sudo apt-get update
sudo apt-get upgrade
```

然后慢慢等

# 安装ranger文件管理器

``` 
sudo apt-get install ranger
```

启动ranger

``` 
ranger
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811124301925.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

这里可以访问其他磁盘

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811124348418.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

ranger的配置

* 复制配置文件到主目录

 
按 `q` 退出ranger

``` 
ranger --copy-config=all
```

进入ranger

``` 
sudo su
输密码
ranger
```

先按z再按h 查看隐藏文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811125550717.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811125638781.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

这个rc.cong就是ranger的配置文件  接着按方向键→

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811125619481.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

选择2, 则默认用完整版的vim打开  .tiny是简版的vim
这里你可以慢慢折腾, 设置你自己的快捷键

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811130052848.png)

比如把 `!` 改成vim新建文件
可以改原来的也可以新加快捷键
改完了保存退出
终端关了重新打开--测试--生效

# Vim

## 安装Vim插件管理器

``` 
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

默认安装在 `/.vim/bundle/vundle` 目录下.
`.vimrc` 是配置文件, 为了避免配置文件过于臃肿

* 新建一个用来管理插件的配置文件

``` 
sudo vim ~/.vimrc.bundles
```

别把 `.` 落了

``` 
set nocompatible              " 去除VI一致性,必须要添加
filetype off                  " 必须要添加

 set rtp+=~/.vim/bundle/Vundle.vim
  call vundle#begin()
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
   "Vundle  管理插件工具 一定不能删
  Plugin 'VundleVim/Vundle.vim'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "Markdown  使vim支持markdown的插件
  Plugin 'godlygeek/tabular'
  Plugin 'plasticboy/vim-markdown'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "Markdown  Preview  markdown动态预览的插件
  Plugin 'iamcco/mathjax-support-for-mkdp'
  Plugin 'iamcco/markdown-preview.vim'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "NerdTree  左边侧栏
  Plugin 'scrooloose/nerdtree'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "Picture Preview   ranger中预览图片 
  Plugin 'tokuhirom/w3m'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "UltiSnips     代码块引擎
  Plugin 'SirVer/ultisnips'
  Plugin 'honza/vim-snippets'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "YCM"    智能感知 (这个插件我先注释带,直接这样装不行,他的安装再后面有)
  " Plugin 'Valloric/YouCompleteMe'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "airline"  就是上面和下面的那个有文件相关信息的条
  Plugin 'vim-airline/vim-airline'
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
  "tagbar  右边侧栏 显示文件的大纲
  "类啊结构体啊什么的如果有不支持的语言上他的GitHub看
  Plugin 'majutsushi/tagbar'

   call vundle#end()    " 必须
   syntax on
   filetype indent on
   filetype plugin on
   filetype plugin indent on    " 必须
   " 加载vim自带和插件相应的语法和文件类型相关脚本
   " 忽视插件改变缩进,可以使用以下替代:
   "filetype plugin on
   
   " 常用的命令
   " :PluginList       - 列出所有已配置的插件
   " :PluginInstall     - 安装插件,追加 `!` 用以更新或使用 :PluginUpdate
   " :PluginSearch foo - 搜索 foo ; 追加 `!` 清除本地缓存 
   " :PluginClean      - 清除未使用插件,需要确认; 追加 `!` 自动批准移除未使用插件
   " 查阅 :h vundle 获取更多细节和wiki以及FAQ
   " 将你自己对非插件片段放在这行之后

```

在 ` call vundle#begin()` 和 ` call vundle#end()` 之间的就是即将要安装的插件, 上边的是我安装了的插件, 插件的功能我做了简单的注释, 具体去他们各自的GitHub上看

* 新建配置文件

``` 
sudo vim ~/.vimrc
```

别把 `.` 落了
添加以下  前三行就是把刚刚插件的那部分加进来  后面的我都加了注释

``` 
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"加载vimrc.bundles
if filereadable(expand("~/.vimrc.bundles"))
    source ~/.vimrc.bundles
endif
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"tagbar  vim中右边的侧栏(设置快捷键和支持markdown标题)
map <C-t> :TagbarToggle<CR>
let g:tagbar_type_markdown = {
    \ 'ctagstype' : 'markdown',
    \ 'kinds' : [
        \ 'h:Heading_L1',
        \ 'i:Heading_L2',
        \ 'k:Heading_L3'
    \ ]
    \ }

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"NearTree  vim中左侧侧边栏设置快捷键为ctrl+b
map <C-b> :NERDTreeToggle<cr>

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"Markdown  
"disable folding
let g:vim_markdown_folding_disabled=1
" Highlight YAML frontmatter as used by Jekyll
let g:vim_markdown_frontmatter=1

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"iamcco/Markdown-Preview  markdown预览的相关设置
let g:mkdp_auto_start = 1
let g:mkdp_path_to_chrome = "firefox"
let g:mkdp_auto_open = 1
let g:mkdp_auto_close = 1
"let g:mkdp_refresh_slow = 1
let g:mkdp_open_to_the_world = 1
map <C-m> :MarkdownPreview<cr>
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"UltiSnips
let g:UltiSnipsExpandTrigger="<tab>"
let g:UltiSnipsJumpForwardTrigger="<CR>"
let g:UltiSnipsJumpBackwardTrigger="<c-z>"
let g:UltiSnipsEditSplit="vertical"
let g:UltiSnipsUsePythonVersion = 3

set tabstop=4
set softtabstop=4
set shiftwidth=4
set expandtab
set autoindent
set cindent
set cinoptions={0,1s,t0,n-2,p2s,(03s,=.5s,>1s,=1s,:1s
set nu
set ts=4
colorscheme torte

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"YouCompeleteMe  相关设置以及解决tab键和UltiSnips的键位冲突
function! g:UltiSnips_Complete()
      call UltiSnips#ExpandSnippet()
        if g:ulti_expand_res == 0
            if pumvisible()
                    return "\<C-n>"      
              else
                    call UltiSnips#JumpForwards()
                    if g:ulti_jump_forwards_res == 0
                        return "\<TAB>"
                endif
            endif
        endif
        return ""
    endfunction

function! g:UltiSnips_Reverse()
    call UltiSnips#JumpBackwards()
    if g:ulti_jump_backwards_res == 0
        return "\<C-P>"
    endif

    return ""
endfunction

if !exists("g:UltiSnipsJumpForwardTrigger")
    let g:UltiSnipsJumpForwardTrigger = "<tab>"
endif
if !exists("g:UltiSnipsJumpBackwardTrigger")
    let g:UltiSnipsJumpBackwardTrigger="<s-tab>"
endif

au InsertEnter * exec "inoremap <silent> " . g:UltiSnipsExpandTrigger     . " <C-R>=g:UltiSnips_Complete()<cr>"
au InsertEnter * exec "inoremap <silent> " .     g:UltiSnipsJumpBackwardTrigger . " <C-R>=g:UltiSnips_Reverse()<cr>"
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
"设置可以使用鼠标"        
set mouse=a
```

上边是对各个插件的设置, 快捷键的设置之类的, 我都加了注释, 具体看各自插件的GitHub, 	README.md文件中都有具体的介绍

* 安装插件

在命令行中打开vim 使用PluginInstall命令安装插件 

``` 
vim
:PluginInstall
```

**等**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811134854724.png)

`+` 是装完的
`>` 正在装的

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811135023640.png)

完成 退出 

``` 
:qa
```

# 运行有图形化界面的软件

1. 设置环境变量(配置显示设备)

``` 
vim ~/.bashrc
```

最后一行添加

``` 
export DISPLAY=:0
```

使配置生效

``` 
source ~/.bashrc
```

2. Windows安装Xming

[Xming下载地址](https://links.jianshu.com/go?to=https://nchc.dl.sourceforge.net/project/xming/Xming/6.9.0.31/Xming-6-9-0-31-setup.exe)

安装后选这个

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811140712969.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811140733849.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

选第一个  , displaynumber换0 (即和前面的设置对应)
然后一路默认下一步

3. 装个火狐试一试

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811142300227.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811142457392.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

* 火狐浏览器中文应该会乱码

``` 
sudo apt-get install ttf-wqy-microhei
```

* 重启火狐

# MarkDown

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190811145921199.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQwOTQxMDI3,size_16,color_FFFFFF,t_70)

之前已经装过插件了
普通模式下(按 `Esc` 回到普通模式)  输入前几个字母按 `tab` 键可以补全

``` 
:MarkdownPreview
```

就可以启动火狐浏览器预览

# Ultisnips代码块引擎

插件前面都一起装过了
如果补全功能出现问题 比如按tab不能补全参考下面链接
[链接](https://www.cnblogs.com/acbingo/p/4757275.html)

# YouCompleteMe

1. 安装

[这里](https://blog.csdn.net/liao20081228/article/details/80347889)

2. 可能出现的错误

* [ERROR: Python headers are missing in /usr/include/python2.7.](https://blog.csdn.net/qq_39815320/article/details/89073050)
* [ImportError: No module named requests](https://www.itbulu.com/python-requests.html)

## YCM和Ultisnips按键冲突解决方案（只使用TAB键，无错误）

我上边给的文件已经改过了
[解决方法](https://blog.csdn.net/qq_20336817/article/details/51115411)

# vim格式化

1，gg 跳转到第一行

2，shift+v 转到可视模式

3，shift+g 全选

4，按下 =

# 终端美化

[链接](https://www.jianshu.com/p/b147735ff3f2)
[其他主题](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)

# 参考

https://blog.csdn.net/Striker_V/article/details/52592591
https://www.imydl.tech/linux/431.html
https://zhuanlan.zhihu.com/p/35536223
https://www.jianshu.com/p/aca81f8c7f08

