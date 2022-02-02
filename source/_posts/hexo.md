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
Hexo对我而言最大的优势就是NeXT，Jekyll虽然有移植版的，但是已经n久没有更新了，而且对于LaTeX不支持。哦，对了，可以本地预览，终于不用等github的脸色了。    
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

# NeXT
这就是我换Hexo最大的理由了  
切记切记，不要用7.x的那几个版本，那个因为原作者不在线而接手next的作者也不在线了，一个更新的作者接手了这个项目。我现在用的最新的8.9版本！  
[NeXT](https://theme-next.js.org/)  
根据官网说法，在根目录创建名为`_config.next.yml`的文件，并将`/themes/next/_config.yml`的内容复制过去。之后要修改主题的配置也是在这里啦~
虽然不知道要不要在`_config.yml`中修改为`theme: next`，但是改了总没错。

# 发文章
现在发文章就不像Jekyll一样直接push上去就完事了，要现在本地hexo生成一下。
`hexo generate`或简写为`hexo g`
`hexo deploy`或简写为`hexo d`

# 配色
又是经典的配色问题，首先是行内代码块高亮改为淡黄色，在next8.9中，在`themes\next\source\css\_common\scaffolding\highlight\index.styl`中找到`code-inline`并修改为
```
$code-inline {
  background: #ffffc1;
  color: var(--highlight-foreground);
}
```
这时候发现代码块也变成了淡黄色，发现下面的`code-block`直接`@extend $code-inline`，好家伙，作者是真省事啊。  
那我们就重新声明一下背景颜色，加入一句`background: white;`。（ps：声明颜色可以用十六进制，也可以用rgba，也可以直接写颜色）  
大功告成！

# 跨设备使用
留个坑吧，换电脑的时候再说