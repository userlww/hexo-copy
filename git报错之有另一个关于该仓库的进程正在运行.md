---
title: git报错之有另一个关于该仓库的进程正在运行
copyright: false
date: 2018-01-06 20:40:56
tags: [git,版本管理]
categories: git

---
今天写完博客提交的时候进程没结束发现有一点问题，就Ctrl+C强制停止，结果第二次提交的时候就报了如下的错误
>      fatal: Unable to create 'E:/hexo/.deploy_git/.git/index.lock': File exists.
>      Another git process seems to be running in this repository, e.g.
>      an editor opened by 'git commit'. Please make sure all processes
>      are terminated then try again. If it still fails, a git process
>      may have crashed in this repository earlier:
>      remove the file manually to continue.

&nbsp;&nbsp;&nbsp;大概意思是lock.index文件已存在，无法继续，谷歌了一下，这个文件的作用是锁定当前目录，避免有多个进程同时对当前目录进行操作，运行之后自动删除，于是到.git目录下删除index.lock,再次运行，没有错误。下面是原回答，不过有墙。
[Another git process seems to be running in this repository][1]


  [1]: https://stackoverflow.com/questions/38004148/another-git-process-seems-to-be-running-in-this-repository