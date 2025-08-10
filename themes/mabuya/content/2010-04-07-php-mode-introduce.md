---
title: php-mode 介绍
description: "在emacs中配置好用的php开发环境"
date: 2010-04-07
taxonomies:
  tags: [Code]
---


## 介绍
在Emacs中，php mode是一个编辑php源码主要的模式。扩展自Emacs的C模式，他继承了所有C模式的导航和编辑功能。语法着色依照php 3,4,5的版本。默认情况下，缩写规则遵循PHP PEAR代码规范。另外PHP中的开发助手包含的文档检索自PHP manual，用来完成代码完成和class browser.
可以用M-x php-mode-version来确定PHP mode的版本
PHP mode是Turadg Aleahmad在1999年首次写成的。

这篇文档适合老练的EMACS用户特别是熟知Emacs manual.他们也需要知道怎么使用php来编写程序，本文不包含如何使用Php编程的相关知识。

## Electricity
在emacs中输入某些特殊字符会有特殊作用。比如：敲入TAB (or C-i)会使某行到正确的列上（正确的符合语法缩进）。
如果这些特殊字符的效果不适你需要的，则在敲入特殊字符之前敲入C-q.比如：C-q TAB敲入一个真实的tab。C-c C-l是禁用electric效果，在按一次则取消

## 动作
在Emacs和C mode的传统惯例在php mode中得以保留。下列命令值得注意：
C-M-f    前向跳跃（按语法单位），如果是字符串，则跳到字符串末尾。如果光标在花括号中，则跳到花括号末尾。如果光标在声明块中，则跳到块末尾。
C-M-b 类似C-M-f，不过是后向跳
C-M-a 跳到最顶级的函数定义的开头
C-M-e 跳到最顶级的函数定义的结尾
C-M-<HOME> 跳到当前函数的开头
C-M-<END> 跳到当前函数的结尾
M-m 移动到当前行的开头（考虑空白符）

## 缩进
.emacs中的设置
php-mode-force-pear 在所有打开的php文件使用php pear索引规则
c-basic-offset 在c模式中一个级别的语法单位缩进的列数，在php mode中默认是4个空格（c mode也一样）
indent-tabs-mode  tab是按照制表符缩进还是若干字符的空格缩进，php mode默认设为nil
C-c C-q 把当前光标所在的最顶级的语法单元缩进（类或函数）

## 编辑
M-q 用fill-column指定的值填充段落。这个命令能在格式化代码和php注释中包含docblock注释时正确工作
C-u n C-x f 设置fill-column的值用于M-q 命令(fill-paragraph)
C-M-h 全选当前最高语法块（比如整个类），通常你可以用C-w or M-w来删除选定区域或者C-M-\ or C-x TAB来格式化选定区域
M-x mark-defun 类似C-M-h，只是C-M-h选中top-level语法块，而mark-defun是选定当前语法块（比如类中的一个函数）

传统的emacs中的压缩选定区域命令在Php mode被支持。下列命令是值得注意的

## Index菜单
php mode提供了当前函数和类定义的显示列表。这个菜单很简单，但是很有效。要想使它工作，则敲入命令：
M-x imenu-add-menubar-index
这个命令会扫描文件并增加一个菜单项Index,点击开可跳转到相关定义

## 备注
附图：我的php-mode
[imgShow:<img src="/assets/php-mode.png" border="0" alt="skag" width="560" />]