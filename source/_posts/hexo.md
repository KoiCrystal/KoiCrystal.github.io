---
title: 搬家Hexo
date: 2022-2-2
description: NeXT毕竟是个Hexo的主题啊，Jekyll都多少年没更新了
category: 
tags:
  - 
---
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

