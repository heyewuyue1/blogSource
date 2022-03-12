---
title: 形式语言与自动机
date: 2022-03-12 10:59:47
tags:
 - 形式语言与自动机
comment: waline
---

# 形式语言与自动机

## 第二章 语言及文法

### 2.1 语言的定义与运算

- 字母表
- 字符串
- 字符串的运算
- 前缀后缀和子串
    >空串是任何字符串的前缀后缀和字串
- 字符串$\omega$的逆用$\bar{\omega}$表示
- 字母表的幂运算
    1. $T^0=\lbrace\varepsilon\rbrace$
    2. 设$x\in T^{n-1}, a\in T$，则$ax\in T^n$
    3. T^n中的元素只能由前两条生成
- \*闭包：$T^* = T^0\cup T^1\cup T^2\cup\cdots$
- \+闭包：$T^+ = T^1\cup T^2\cup T^3\cup\cdots$
- $T^* = T^+\cup\lbrace\varepsilon\rbrace,T^+ = T^*-\lbrace\varepsilon\rbrace$

- 语言：设$T$为字母表，则任何集合$L\subseteq T^*$是字母表$T$上的一个语言
- 举例：设$T=\\{a, b\\}$
    则 $L_1=\\{a^nb^n|n\ge 1\\}$
    $L_2=\\{b^k|k是质数\\}$
    $L_3=\\{\varepsilon\\}$ // 只有一个空句子的语言
    $L_4=\\{\\} = \emptyset$ // 空语言
- 语言的积：集合的有序笛卡尔积（我自己编的话），所以$L_1L_2\neq L_2L_1$
- 语言的幂

### 2.2 文法

文法是用来定义语言的数学模型

- BNF（巴科斯范式）
    - <数字>::=0|1|2|...9  // ::=读作“定义为”
    - <字母>::=A|B|C|...Z|a|b|...z
    - <标识符>::=<字母>|<标识符><字母>|<标识符><数字>

- **Chomsky文法体系**
    文法是一个四元组$G=(N,T,P,S)$，其中
    - N 非终结符的有限集合
    - T 终结符的优先级合 $N\cap T=\emptyset$
    - P 形式为$\alpha \rightarrow \beta$的生成式的有限集合。且$\alpha\in (N\cup T)^\*N^+(N\cup T)^\*,\beta\in(N\cup T)^\*$
    - S 起始符 且$S\in N$

- 例子见课件

### 2.3 Chomsky文法体系分类

- 0型文法：无限制
- 1型文法：1）左部长度小于右部 2）不含$A\rightarrow \varepsilon$
- 2型文法：左部是单个非终结符
- 3型文法：
    1. $A\rightarrow \omega B$或$A\rightarrow \omega$
    2. $A\rightarrow B\omega$或$A\rightarrow \omega$

- 四类文法之间的包含关系搞清楚。