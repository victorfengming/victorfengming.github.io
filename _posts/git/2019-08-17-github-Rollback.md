---
title: "git版本的回滚"
tags: Git solution 
---





* content
{:toc}






### 版本出错之解决方法

很多小伙伴在进行版本控制的时候，有可能会遇到项目不能正常的上传，导致github还是将你最后一个正常push的版本展示出来
这时候我们如果想要继续修改，则需要将版本回滚到还没出错的最后一个版本之前才行
下面我们介绍一下如何进行版本的回退

##### 版本回退
git能够回到任意你提交过的版本，这样对于版本的控制将会十分的方便   ！
下面介绍两种方法进行回滚

##### github官方的存储库
你可以在github的存储库中找会对应版本，下载对应的压缩包，

##### 终端中的git命令
当然，你也可以使用命令进行，具体命令如下
```
回退到某个版本（最后的一串字符是 版本变更编号，通常这个编号可以在 git 后台看到，也可以通过  $ git log -300 显示最近300次提交记录）
git reset --hard 目标版本的哈希值 
强制提交到master分支（具体哪个分支请酌情修改）

git push -f -u origin master
```

