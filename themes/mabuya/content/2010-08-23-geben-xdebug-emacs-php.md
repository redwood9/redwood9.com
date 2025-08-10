---
title: Geben + Xdebug + Emacs 调试php
description: "介绍一种在emacs中远程调试php的方法"
date: 2010-08-23
taxonomies:
  tags: [Code]
---

一直都是用var-dump, echo, die 输出变量来调试php，终于有一天，无法忍受这种低效且不专业的调试方式，经过一番研究，发现在emacs里面，Geben是一个不错的选择

## geben的安装
下载geben
cd geben-0.26/
make
Copy \`dbgp.elc\', \`geben.elc\' 和 \`tree-widget\' 目录到emacs load path下

## xdebug的安装
```bash
wget http://www.xdebug.org/files/xdebug-2.1.0.tgz
tar xvfz xdebug-2.1.0.tgz
cd xdebug-2.1.0.tgz
phpize
./configure --enable-xdebug
make;make install
```

## 修改php.ini 增加 
``` Bash
zend_extension_ts="/wherever/you/put/it/xdebug.so"
zend_extension="/wherever/you/put/it/xdebug.so"
```

## php.ini增加xdebug配置内容：
```Bash
xdebug.remote_enable = On
```

## 使用方式
**.emacs 中加入**：
```Bash
(autoload 'geben "geben" "PHP Debugger on Emacs" t)
```
**启动emacs**

M-x geben

直接访问一个php页，如果设置了手工触发，则需要增加url参数，类似于：
http://www.example.com/test.php?XDEBUG_SESSION_START=1


如果是命令行调试，则
```Bash
export XDEBUG_CONFIG="idekey=session_name";php myscript.php
```

## geben mode 下快捷键
``` Bash
spc     step into/step over
i       step into
o       step over
r       step out
g       run
c       run to cursor
b       set a breakpoint at a line
B       set a breakpoint interactively
u       unset a breakpoint at a line
U       clear all breakpoints
\C-c b  display breakpoint list
>       set redirection mode
\C-u t  change redirection mode
d       display backtrace
t       display backtrace
v       display context variables
\C-c f  visit script file
w       where
q       stop
```

## 参考
[geben]("http://code.google.com/p/geben-on-emacs)

[xdebug]("http://www.xdebug.org/)

![在emacs中整体的效果图](/assets/txt.png)

