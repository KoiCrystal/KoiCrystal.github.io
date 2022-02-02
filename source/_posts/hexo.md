---
title: 搬家Hexo
date: 2022-2-2
description: NeXT毕竟是个Hexo的主题啊，Jekyll都多少年没更新了
category: 
tags:
  - 
---
# Hexo VS Jekyll
犹豫了再三，还是从官方支持的Jekyll跳槽到了Hexo，先做个两者的对比和总结吧。  
Hexo对我而言最大的优势就是NeXT，Jekyll虽然有移植版的，但是已经n久没有更新了，而且对于LaTeX不支持。哦，对了，可以本地预览，终于不用等github的脸色了  
（提醒一下啊喂：NeXT因为作者不上线的缘故所以历经了好几个阶段，star最多的不一定之最新的啊！我就在7版本上折腾了半天，后来发现了新的8.9版本，yysy，新作者真给力）  
Jekyll最大的优势就是方便，不依赖本地环境，所有代码都在仓库里，换电脑直接拉仓库可以直接用。  
所以这里也留了个坑，我换电脑的时候Hexo该怎么跨过去呢？

# Hexo
`npm install hexo-cli -g`  
`hexo init blog`创建一个名为blog的文件夹并生成博客框架，如果已经创建了文件夹，可以直接`hexo init`  
进入刚刚创建的文件夹  
`npm install `

# SSH
记得在github加入ssh呀！

# push源文件上去
这时候新建的仓库还不认识这个本地文件夹呢，总得介绍一下不是。  
git init  
git add . 
git commit -m "first commit"
git branch -M main
git remote add origin <your_repo_address>      //github拉仓库时复制的那个
git push -u origin main

# push博客上去
先安装`deploy-git`，用`npm install hexo-deployer-git --save`  
找到`_config.yml`文件，里面有`deploy`字段，修改为：
```
deploy:
  type: git
  repo: <your_repo_address>
```
其实还有一句`branch: master`，但是不写这一句可以直接默认。  
之后在pages的设置里修改source为`master`分支

