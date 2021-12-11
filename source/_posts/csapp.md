---
title: 计算机系统基础笔记
date: 2021-11-19 01:01:03
tags:
 - 深入理解计算机系统
 - 计算机系统基础
---

属于是一个手忙脚乱的临时更新了，因为发现自己确实啥都不会了。这篇暂时会一改我别的笔记风格，不会有任何章法，仅仅是按照我不会的程度和考试的紧迫程度进行一个相对凌乱的记录。
比较完整的请见[🍄神的csapp笔记](https://mushroom323.github.io/2021/10/29/csapp/)

# 第二章 信息的表示和记录

## 2.4 浮点数

### 2.4.2 IEEE浮点表示
*凌乱之余好歹还是保持目录结构的完整性*
IEEE浮点标准使用$V=(-1)^s\times M\times 2^E$来表示一个数
- **符号** $s$决定这个数是正数还是负数，$s=1$就是负数，$s=0$就是正数。
- **尾数** $M$是一个二进制小数，它的范围是$1\sim 2-\varepsilon$，或者是$0\sim 1-\varepsilon$。
- **阶码** $E$对浮点数加权，这个权是2的$E$次幂（可能是负数）。
将浮点数的位表示划分为三个字段，分别对这些值进行编码（注意是编码，而不是就是这些数）
- 一个单独的符号位$s$直接编码符号$s$。
- $k$位的阶码字段编码阶码$E$。
- $n$位小数字段编码尾数$M$。
根据$\rm exp$的值，被编码的值可以分为三种不同的情况：
1. 规格化的
![规格化的图](https://api2.mubu.com/v3/document_image/bc77a791-5ff6-4341-bc05-0fcb48a9a494-15002533.jpg)
这是最普遍的情况，即$\rm exp$的位即不全为0，也不全为1时。此时：
    - $E= {\rm exp}-Bias,Bias=2^{k-1}-1$（单精度Bias为127，双精度为1023）
    - $M=1.f_{n-1}f_{n-2}\cdots f_0$，小数点在最高有效位的左边
2. 非规格化的
![](https://api2.mubu.com/v3/document_image/99e4148f-a387-450a-b8be-185b78f2e3bd-15002533.jpg)
    - $E=1-Bias$
    - $M=0.f_{n-1}f_{n-2}\cdots f_0$
3. 
    a. 
    ![](https://api2.mubu.com/v3/document_image/f2f4450f-6e8b-4a51-8536-bafd3620d620-15002533.jpg)
    两个非常大的数相乘，或者除以0，会产生$\infty$。$s=1$表示$-\infty$，$s=0$表示$\infty$。
    b. ![](https://api2.mubu.com/v3/document_image/40177575-52a0-43e0-9572-9edac50148e3-15002533.jpg)
    运算结果不是实数或无穷如$\sqrt{-1}$或$\infty -\infty$，表示为NAN。

### 2.4.6 C语言中的浮点数

从`int`转为`float`：会舍入，不会溢出
从`int`转为`double`：不会舍入，不会溢出
从`float`转为`int`：会舍入，会溢出
从`float`转为`double`：不会舍入，不会溢出
从`double`转为`float`：会舍入，会溢出
从`double`转为`int`：会舍入，会溢出

### 关于大端序和小端序
![](https://api2.mubu.com/v3/document_image/eadc3b36-ff28-44bf-8f15-7d5a96bf4243-15002533.jpg)
<br><br><br><br><br>
<script src="//unpkg.com/valine/dist/Valine.min.js"></script>
<div id="vcomments"></div>
<script>
    new Valine({
        el: '#vcomments',
        appId: 'pYVxUdjGaaE4WkIo9yulsMpw-gzGzoHsz',
        appKey: 'k5IXm5eqTCqoajlqYcc8F39c'
    })
</script>
