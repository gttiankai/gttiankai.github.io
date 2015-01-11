
---
layout: post
title: Blogging Like a Hacker
---
<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. 前言</a></li>
<li><a href="#sec-2">2. 系统情况</a></li>
<li><a href="#sec-3">3. 关于为什么要这么配置</a></li>
<li><a href="#sec-4">4. 在github上建立自己的blog</a>
<ul>
<li><a href="#sec-4-1">4.1. github pages 创建失败</a></li>
</ul>
</li>
<li><a href="#sec-5">5. 搭建Jekyll环境</a>
<ul>
<li><a href="#sec-5-1">5.1. 安装 Ruby</a></li>
<li><a href="#sec-5-2">5.2. 安装 bundler</a></li>
<li><a href="#sec-5-3">5.3. 安装Jekyll</a></li>
</ul>
</li>
<li><a href="#sec-6">6. Running Jekyll</a></li>
<li><a href="#sec-7">7. Configuring Jekyll</a></li>
<li><a href="#sec-8">8. 创建自己的第一份blog</a></li>
<li><a href="#sec-9">9. 将org文件转换成markdown文件</a></li>
</ul>
</div>
</div>


# 前言<a id="sec-1" name="sec-1"></a>

今天晚上在看文章的时候突然想起来上次没有成功使用github+org-mode+jekyll写blog的事情,今晚正好有时间,所以就索性配置一下,将自己配置遇到的问题,记录下来,以方便大家如果遇到我出现的问题,可以快速的结果.

# 系统情况<a id="sec-2" name="sec-2"></a>

Mac OX 10.95   
org-mode: emacs24.4.1 自带的org-mode   
(ps:至于为什么会写明自己使用的环境,是为了让大家更好的解决问题,因为我自己以前遇到问题,在网上查到了解决方式,可是最后发现和别人使用的环境不同,造成浪费了好多时间,还没有解决问题)

# 关于为什么要这么配置<a id="sec-3" name="sec-3"></a>

一开始我是在网上无意中看了文章

# 在github上建立自己的blog<a id="sec-4" name="sec-4"></a>

github的官网上有如何使用git page的wiki建立个人blog的指导教程,很详细,大家可以按照上面的步骤一步一步的进行操作,就可以了,并且上面也有使用jekyll,绑定用户自己的域名的介绍,很详细.大家可以看看.所以这里就不在罗嗦了.
链接在这里:[github的page页面](https://pages.github.com/)   
如果你在创建git Pages的过程中出现了问题,你可以在自己在github上得邮箱中收到邮件,里面有失败的原因的说明,你可以可以看这里[Troubleshooting GitHub Pages build failures](https://help.github.com/articles/troubleshooting-github-pages-build-failures/)
(ps:一定要创建index.html文件,不然你会遇到下面的问题)

## github pages 创建失败<a id="sec-4-1" name="sec-4-1"></a>

解决方式: 创建一个名为 index.html的文件

出现这个问题的原因分析(如果感兴趣的话):  
我安装官网上得进行设置,但是竟然会遇到蛋疼的不能自动创建git pages的问题,而且别人即使创建不成功,也会收到邮件说,创建不成功,但是我遇到的问题就比较蛋疼,居然连通知邮件都没有,我在找找原因,实在不行,就只能将新建的仓库删除,然后重新建立了.

我仔细的查看了该仓库的配置信息,发现该仓库的信息里面提示了该"Your site is published at username.github.io"已经创建成功了,但是为什么我去访问<http://usrename.github.io> 不能招到网页呢?我就想起了,在我自己创建username.github.io的仓库的时候,因为里面已经有文件了,所以就图省事,没有创建index.html文件.  
当我们访问<http://username.github.io> 的时候,github会再文件目录下面自动的查找index.html文件,找不到就会显示<http://username.github.io> 地址找不到,index.html一般是网站的默认的主页文件,所以只要创建一个index.html文件就可以了.现在再去看一下<http://username.github.io>, 这个时候应该创建成功了.

# 搭建Jekyll环境<a id="sec-5" name="sec-5"></a>

我看的是github官网上得教程,关于使用Jekyll,但是我在安装工程中遇到一些问题,所以在这里记录下来.

github上关于使用Jekyll的链接在这里:[Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)

## 安装 Ruby<a id="sec-5-1" name="sec-5-1"></a>

上面的教程中虽然说了在Mac系统已经安装了Ruby,所以不需要安装Ruby了,但是我已开始尝试的时候,发现在进行第二步安装bundler的过程中,不能正常安装提示权限问题,问了一下google,发现一篇blog([链接](http://blog.lessfun.com/blog/2014/05/20/clone-exists-octopress-blog-to-new-mac/)),上面说如果直接使用sudo命令继续安装,在后边会继续遇到问题(ps:本人没有亲自尝试).  
所以本人重新安装了Ruby,安装命令如下:

    brew install ruby

安装完成之后,我使用ruby -version 命令显示的还是原来系统安装的ruby-2.0.0,不是新安装的ruby-2.2.0(应该是shell得配置文件还没有起作用),这个时候不能直接进行下一步的安装,可以重启当前的shell.

然后就可以下面的安装了.

## 安装 bundler<a id="sec-5-2" name="sec-5-2"></a>

安装
gem install bundler

如果遇到下面的问题,请重新进行上一步安装Ruby的操作
ERROR:  While executing gem &#x2026; (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.

## 安装Jekyll<a id="sec-5-3" name="sec-5-3"></a>

在github下的要作为blog的仓库的目录下创建一个名为Gemfile的文件.文件的内容如下:

    source 'https://rubygems.org'
    gem 'github-pages'

然后执行命令 

    bundle install

进行安装Jekyll.  
ps: 在安装的过程中有可能会出现问题,别担心,上面会有提示该怎么操作,只要按上面的提示,进行操作,然后重新执行命令: bundle insatll 就可以了.

# Running Jekyll<a id="sec-6" name="sec-6"></a>

根据github上得教程运行安装好的Jekyll,

    bundle exec jekyll serve or (jekyll server)

当你执行这条指令的时候,终端中会提示你开启的jekyll服务器是否成功,如果成功,然后在浏览器中打开<http://localhost:4000/>, 会出现下面的错误

    Forbidden
    no access permission to `/'

看到这个先不要着急,在安装jekyll的过程中,会生成一个<sub>site文件夹</sub>,如果里面有html文件的话,你试着访问这个文件,我在<sub>site文件夹下面有个hello</sub>.html的页面,使用虾下面的URL试一下:

<http://localhost:4000/hello.html>

如果正常实现,说明我们已经将Jekyll正确的安装了.

还有一种解决方式就是在git仓库的目录下创建一个名为index.html的文件,这个时候,再访问<http://localhost:4000/> 应该就可以了.

# Configuring Jekyll<a id="sec-7" name="sec-7"></a>

按照github帮助网页上得说明进行配置就可以.  
主要就是在网站的根目录下面创建一个名为<sub>config</sub>.yml的文件,然后在里面添加下面的代码:

    highlighter: pygments
    github: [Repository metadata]

# 创建自己的第一份blog<a id="sec-8" name="sec-8"></a>

通过上面的步骤,现在自己已经可以创建自己的第一份blog了.由于本人学习喜欢从头到尾进行学习,所以我自己就去jekyll的官网上大致的浏览了一遍官方的教程,如果你也想去看的话,[链接在这里](http://jekyllcn.com/docs/home/).

# 将org文件转换成markdown文件<a id="sec-9" name="sec-9"></a>

现在到了将org写的文章转换为blog了,jekyll是不直接支持org文件格式的,如果上传一个org的文件,github会将该文件看做一个可下载的文件.现在网上有三种方式将org文件和jekyll结合在一起,我个人感觉都不是很好,幸好我自己又找到一种方式,既简单有高效还准确.
1.  org 导出html，直接交给 jekyll 处理。这么做有个问题，org生成的html可能和 markdown 产生的html有差异，有的时候兼容性不好。比如，插入 <!&#x2013;more&#x2013;> 语句时，由于 org 生成的 html 充满了 div ，导致在有 headline 的情况下页面可能会乱掉。
2.  org 文件通过 emacs 的插件转换为 markdown 格式，再由 jekyll 处理。可以到[这里](https://github.com/alexhenning/ORGMODE-Markdown) 找到相关资源。
3.  [org-ruby](http://orgmode.org/worg/org-tutorials/org-ruby.html)。 通过Ruby将 org 文件转化为 html，而不是通过emacs

(ps:以上的三种方式来源于网络,原blog的地址在这里:[emacs + org-mode + octopress + github](http://ifq.github.io/blog/2012/08/10/org-octopress/))  
我考虑到jekyll是对markdown文件做了优化的,并且直接将markdown文件放在<sub>post文件下</sub>,就可以直接解析了.所以我最终决定使用第二种方式.  
因为我自己不懂lisp语言,经过第二种方式的指导,也没有配置成功,所以上面说的第二种方式,我没有能实现出来,再想别的办法.  
我突然想到,想markdown这种标记性语言是很有名气的,而且org作为我最钟爱的写blog得神器,她应该肯定支持,将org-mode转换成markdown文件,所以我org的官网上一搜索,果然是可以将org文件转换为markdown.但是这里要注意,org的版本必须>=8.0才可以.  
至于查看org的版本号的命令页一并赠送:

    M+x org-version

官网上详细的链接请点[这里](http://orgmode.org/worg/exporters/ox-overview.html)  
虽然官网上说了可以直接将org文件转换为markdown文件,当时当我使用C-c C-e 的时候找了好久,竟然没有发现将org文件导出为markdown文件的选项,继续研究.  
在google上查了一下,发现使用的方式非常简答:
1.  在emacs的配置文件中添加下面的命令

    ;; make org exoport to markdown
    (eval-after-load "org" '(require 'ox-md nil t))

1.  将当前的emacs的配置更新:

    eval-buffer

1.  将当前的org文件导出为markdown文件

    org-md-export-to-markdown

也可以将当前的org文件直接导出为markdown文件,命令如下:

    org-md-export-as-markdown

通过上面的命令就可以将org文件直接导出为markdown文件了.是不是很简单!O(∩<sub>∩</sub>)O~