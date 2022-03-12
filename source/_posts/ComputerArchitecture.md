---
title: 计算机组成原理
date: 2022-03-02 17:03:20
tags:
 - 计算机组成原理
comment: waline
---

# 计算机组成原理

## 第一章 计算机系统概论

### 1.2 计算机的发展简史

#### 1.2.4 计算机的性能指标

- **主频/时钟周期**：CPU的工作节拍受主时钟控制，主时钟是不断产生固定频率的钟。主时钟的频率叫做CPU的主频（f）度量单位为MHz或GHz（吉赫兹）；主频的倒数被称为时钟周期（T）度量单位是$\mu s$，$ns$。
- **CPU执行时间**
$$
CPU执行时间=CPU时钟周期数\times CPU时钟周期
$$
- **CPI**：表示每条指令需要的时钟周期数
$$
CPI=执行某段程序需要的时钟周期数\div 这段程序的指令数
$$
- **MIPS**：平均每秒执行多少百万指令数
$$
MIPS=指令数\div (程序执行时间\times 10^6)
$$
- **FLOPS**：每秒执行浮点操作的次数
$$
FLOPS=程序中浮点操作的次数\div 程序执行时间
$$

### 1.3 计算机的硬件

1. 运算器：完成算数和逻辑运算操作，也称为数据通路
2. 存储器：存放程序和数据
3. 控制器：根据取得的指令向其他部件发出控制信号，完成指令规定操作
4. 输入/输出设备：完成人与计算机的相互通信

## 第二章 运算方法和运算器
