---
title: 近期关于emacs的一些心得
description: "探索对emacs进行配置，使之符合我在cpp编程上的习惯，以及基本的项目、代码补全工具"
date: 2007-09-28
taxonomies:
  tags: [Code]
---

最近一直在研究EMACS，用了一段时间，还是觉得很模糊，今天，又看了一些资料，觉得有些眉目，特记录于此。

1，在我的机器上emacs安装地址为：/usr/share/emacs/22.1

2，在emacs安装目录下有：site-list/subdirs.el ,这个文件保存所有用户启动emacs时做的操作。

3，~/.emacs保存当前用户的emacs设置

4，如果要安装新的插件，比如speedbar，可以把speedbar代码直接放在一个目录
下， 比如/usr/share/emacs/speedbar。在subdirs.el 中加入
(add-to-list 'load-path "/usr/share/emacs/21.3/speedbar")
(autoload 'speedbar-frame-mode "speedbar" "Popup a speedbar frame" t)
(autoload 'speedbar-get-focus "speedbar" "Jump to speedbar frame" t)
(global-set-key [(f4)] 'speedbar-get-focus)
就可以了

5，安装ecb的时候，总是提示安装不成功，提示找不到cl，后来在emacs-22.1\lisp\emacs-lisp中找到，所以在subdirs.el 中加入(add-to-list 'load-path "/usr/share/emacs/21.3/emacs-lisp")，加入后重启emacs根据提示，做相应修改，成功。

6，使用中发现在windows下使用emacs时候，如果直接把配置脚本写在subdirs.el，那么只要脚本加载过程出错，就不能启动emacs。如果想知道.emacs究竟放在哪里，可以选择options->customize emacs->saved options，在minibuf中会看到.emacs的位置。把配置文件写入.emacs,出错会有提示。我本机的.emacs地址为
C:\Documents and Settings\Administrator\Application Data\.emacs 。

7，emacs主题
(load-file "F:/soft/emacs-22.1/lisp/color_theme/color-theme.el")
(require 'color-theme)
(color-theme-dark-blue)

8，emacs缩进
(setq c-basic-offset 4) 缩进4字符

至此，理清了emacs的配置思路，总算是能使用了。		