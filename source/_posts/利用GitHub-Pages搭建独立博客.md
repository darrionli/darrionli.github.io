---
title: 利用GitHub-Pages搭建独立博客
date: 2017-08-01 17:32:13
categories: 文档说明
permalink: github-pages-blog
tags:
- Node.js
- Hexo
---

### 关于Hexo###

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页，[查看官网](https://hexo.io/zh-cn/docs/)。

### 搭建流程###

该流程默认您的机器已经成功安装了Node.js、Git、Hexo 。
1. 创建github仓库，[darrionli.github.io](https://github.com/darrionli/darrionli.github.io)；
2. 创建两个分支：master 与 hexo，把hexo设置成默认分支；<!--more-->
3. 使用`git clone git@github.com:darrionli/darrionli.github.io.git`拷贝该仓库，之后需要把该文件夹的所有内容剪切到其他地方备份，原因是`hexo init`会重新生成一个.git，会覆盖之前的.git，导致不能正常push到hexo分支；
4. 在本地darrionli.github.io文件夹下通过git bash依次执行 `hexo init` （执行完此步后备份文件需要拷贝回来）、`npm install` 和 `npm install hexo-deployer-git`（此时当前分支应显示为hexo）；
5. 修改_config.yml中的deploy参数，分支应为master；
6. 依次执行`git add .`、`git commit -m "..."`、`git push origin hexo`提交网站相关的文件；
7. 执行`hexo g -d`生成网站并部署到GitHub上。

### 关于日常改动###

在本地对博客进行修改后，通过下面的流程进行管理：

1. 依次执行`git add .`、`git commit -m "..."`、`git push origin hexo`指令将改动推送到GitHub（此时当前分支应为hexo）；
2. 然后才执行`hexo g -d`发布网站到master分支上 。

### 本地资料丢失后

当重装电脑之后，或者想在其他电脑上修改博客，可以使用下列步骤：

1. 使用`git clone git@github.com:darrionli/darrionli.github.io.git`拷贝仓库（默认分支为hexo）；
2. 在本地新拷贝的文件夹下通过Git bash依次执行下列指令：`npm install hexo`、`npm install`、`npm install hexo-deployer-git`（记得，不需要hexo init这条指令）。

###### 上述部分内容转自[知乎](https://www.zhihu.com/question/21193762) ，作者[CrazyMilk](https://www.zhihu.com/question/21193762/answer/79109280) ，感谢！

### 问题集锦（收集中）###

1. 执行hexo deploy后提示 `Deployer not found: github` 。

   版本问题，hexo 更新到3.0之后，deploy的type 的github需要改成git，如果不成功，改了之后再执行 `npm install hexo-deployer-git --save` ，然后再部署。

### 参考文档###

- [Hexo官网](https://hexo.io/)
- [知乎](https://www.zhihu.com/question/21193762)


