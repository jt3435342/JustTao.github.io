---
title: 搭建静态博客遇到的一些问题
date: 2016-06-22 20:20:02
tags:
---
# Github + Hexo 搭建静态博客遇到的一些问题
网上关于Github+Hexo搭建的文章很多了，我这里就不再详细介绍搭建步骤了，主要讲讲在解决博客的多PC同步中中遇到的一些问题，希望跟我一样的新手们能少走一些弯路。
我搭建博客时候参考的是这篇博文[GitHub Pages + Hexo搭建博客](http://crazymilk.github.io/2015/12/28/GitHub-Pages-Hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/#more),在这里先谢谢作者了。不过在搭建过程中遇到了一些问题，搜索引擎各种搜索，捣鼓了2天时间才算最终搞定。  
### 多PC同步的搭建过程
1. 在本地文件夹(如D:\hexo)并参考[如何利用GitHub Pages和Hexo快速搭建个人博客](https://xuanwo.org/2015/03/26/hexo-intor/)，在一台pc上搭建好博客
2. 在第一步中已创建的仓库just-tao.github.io中创建hexo分支并设置为默认分支(为了以后更新不出错设为默认)，此时有master与hexo两个分支
3. 将hexo文件夹下的所有.git文件夹删除(包括子文件夹得.git，防止与已创建的仓库产生冲突)，同时编辑hexo自动生成的.npmignore文件（我将其改名为了.gitignore，不改也可以），改为以下内容  
        /.deploy_git
        /public  
        /_config.yml
4. 在hexo文件夹上运行git bash，执行以下命令
        git init
        git remote add origin git@github.com:just-tao/just-tao.github.io.git
        git add .
        git commit -m "Blog created"
        git push origin hexo
这样一台新的电脑上，只需git clone到本地文件夹，就可以在新的电脑上进行博客的写作与发布了。在git clone过程中我发现win7系统的一个问题，就是限制了最长的文件名长度，导致git clone过后，文件下载不全。  
解决方法是在git clone前新建一个文件夹，并git bash执行以下命令。
        git config --system core.longpaths true
第一次写博客，写的不好还请见谅。有什么问题欢迎讨论。