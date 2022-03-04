---
title: 'Emacs配置和快捷键笔记'
date: 2020-07-12 00:00:00
tags: []
published: true
hideInList: false
feature: 
isTop: true
mathjax: true
description: Emacs for OIer
---
<!--more-->

## Emacs配置和快捷键笔记

```lisp
(setq default-tab-width 4)
(setq c-basic-offset 4)
(global-linum-mode t);;行号
(electric-pair-mode t);;输入时括号匹配

(global-set-key (kbd "<f8>") 'shell)
(global-set-key (kbd "<f9>") 'CCompile);;自定义的编译函数
(global-set-key (kbd "RET") 'newline-and-indent);;emacs24下需要
;;按键绑定：遇到交互题可以绑定更多快捷键

(defun CCompile();;一键编译
  (interactive)
  (compile
   	(format
       "g++ -Wall -o %s %s -g -lm"
       (file-name-sans-extension (buffer-name))
       (buffer-name)
     )
   )
)

;;下面是custom-set
(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(backward-delete-char-untabify-method nil);;Emacs默认用四个空格代替tab，这个语句能默认使用tab，设置方法：C-h f + 函数名，选择customize->nil->save for future version...
 '(gdb-many-windows t);;在gdb时默认自动分割窗格，设置方法同上
 '(show-paren-mode t);;高亮配对括号，可以在菜单栏找到，勾选后点击save option
)

```





| 命令 | 功能 |
|:---|----|
| C-b x | 返回原窗格 |
| C-x o | 切换窗格 |
| C-x 5 2 | 新窗口 |
| C-x h | 全选 |
| M-> | 到末尾(shell) |
| M-p（M-n） | 上（下）一条命令(shell) |
| M-{ （M-}） | 向前/后 |
| M-r | 将光标滚动到中间 |
| C-c C-o| 删除最后一条命令产生的输出 |
| C-c C-r| 屏幕滚动到最后一条命令输出的开头|
|C-c C-e| 屏幕滚动到最后一条命令输出的结尾 |



### [Emacs Calc Mode](https://www.gnu.org/software/emacs/manual/html_node/calc/)

https://www.gnu.org/software/emacs/manual/html_node/calc/Function-Index.html#Function-Index

https://www.gnu.org/software/emacs/manual/html_node/calc/Summary.html#Summary

以下命令都是对栈顶元素使用，命令严格区分大小写

Shift+m : 将栈大小增大一倍

常量：pi = $\pi$ ，e = $e$

### [Combinatorial Functions](https://www.gnu.org/software/emacs/manual/html_node/calc/Combinatorial-Functions.html)

| 命令    | 功能                                    |
| ------- | --------------------------------------- |
| k E     | exgcd                                   |
| (H) k c | 组合数（H:下降幂）                      |
| k b     | 伯努利数                                |
| (H) k s | 第一类斯特林数（H:第二类斯特林数）      |
| k p     | 素数检验（重复输入k p命令能提高正确率） |
| k n     | 下一个素数                              |
| k f     | 分解质因数                              |


注：素数检验只保证p<1e9的正确性，p>1e9基于随机，分解质因数只保证分解小于5000的因子

### [Vector/Matrix Functions](https://www.gnu.org/software/emacs/manual/html_node/calc/Matrix-Functions.html#Matrix-Functions)
| 命令    | 功能                               |
| ------- | ---------------------------------- |
| &     | 求逆                              |
| V D | 求行列式 |
| V C | 向量叉积 |
| V J | 共轭矩阵 |

### [Polynomials](https://www.gnu.org/software/emacs/manual/html_node/calc/Polynomials.html#Polynomials)
| 命令           | 功能                                                |
| -------------- | --------------------------------------------------- |
| a f            | 整数因式分解（复杂度较高）                          |
| a x            | 多项式乘法（将栈顶多项式表示成$\sum a_kx^k$的形式） |
| a /            | 多项式带余除法                                      |
| a g            | 多项式gcd                                           |
| a S [variable] | 解方程（单解）                                    |
|a P [variable] | 解多项式方程（多解）                              |


注：因式分解算法使用复数，次数较高时可能有精度误差

### Modulo

用algebra模式键入 `a mod b` 或 `aMeta-Mb`
支持模意义下的 **加减乘除&快速幂**

### Complex

`m p` 切换默认复数表示方式（直角坐标/极坐标）

`m d` 切换为角度deg模式

`m r` 切换为弧度rad模式

输入方式：
	直角坐标：a+bi, (a,b)
	极坐标：(a;b), a\*e^(b\*i)

| 命令           | 功能                                                |
| -------------- | --------------------------------------------------- |
| c p            | 切换当前复数表示方式（直角坐标/极坐标）            |
| J              | 求共轭复数                                    |