---
title: 毕设的Raw_socket嗅探和攻击
date: 2022-3-23
description: 欸嘿嘿，监听和攻击。
category: 信息安全
tags:
  - C++
---
# pcap
## pcap的安装
留个坑哈哈哈哈
## 生成程序
（这里特地研究了一下运行任务`Run Task`和运行生成任务`Run Build Task`有啥区别，emmmmm，发现tasks文件是一样的）
在vscode里直接运行生成任务是跑不了的，会提示
```
ld: symbol(s) not found for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```
此时我们需要熟悉一下原始的编译过程了
我写的是一个名为`raw.cpp`的程序，用命令`gcc -o raw raw.cpp -l pcap`即可编译成功。
其中，`-o`可以指定生成的可执行文件的文件名，此处就叫做`raw`（那个用于指定编译等级发布release版本的是`-O`，从`-O1`到`-O3`,数字越大性能越好）
`-l`指定库名。在其他程序中，也有可能先用`-L`指定库的路径
其实在vscode里修改tasks文件也可以，不过为了一个程序修改tasks不太划算呀
运行时，用命令`sudo ./raw`来运行程序。(`./`表示当前目录)