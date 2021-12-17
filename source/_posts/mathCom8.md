---
title: 第八届全国大学生数学竞赛初赛（非数学类）
date: 2021-10-15 21:47:20
tags:
 - 数学竞赛
---
[试卷链接](https://mp.weixin.qq.com/s?__biz=MzI2OTE2NzczNQ==&mid=2649993462&idx=2&sn=03a0580c0eaf8690448776ad544db1f1&chksm=f2e36deec594e4f83742ba95b482db5e2322e48031e7920fdc5b1fce34d7e225172bbb881999&scene=21#wechat_redirect)
因为好不容易有一套自己会做的稍微多一点的题，发出来纪念一下。
# 一、填空题
## 1.
导数的定义。
## 2.
导数的定义。
## 3.
$$
y'+P(x)y=Q(x) \\\\
y = e^{-\int P(x)dx}(\int Q(x)e^{\int P(x)dx}dx+C)
$$
## 4.
$$
f^{(n)}(0)=A\cdot n!
$$
其中$A$是$f(x)$的麦克劳林展开式中$x^n$项的系数。
## 5.
想不起来曲面切平面怎么求可以拿平面试一下。
# 第二题：
一直求导直到做出来为止，高中难度。
# 第三题：
换元把椭球换成球。三重积分的换元公式：
$$
M = \iiint (x^2+y^2+z^2)dxdydz=\iiint F(u,v,w)\left|\frac{\partial(x,y,z)}{\partial(u,v,w)}\right|dudvdw
$$
$$
\left|\frac{\partial(x,y,z)}{\partial(u,v,w)}\right|=\left|
\begin{array}{cccc}
    \frac{\partial x}{\partial u}  &  \frac{\partial x}{\partial v}   & \frac{\partial x}{\partial w} \\\\
    \frac{\partial y}{\partial u}  &  \frac{\partial y}{\partial v}   & \frac{\partial y}{\partial w} \\\\
    \frac{\partial z}{\partial u}  &  \frac{\partial z}{\partial v}   & \frac{\partial z}{\partial w} \\\\ 
\end{array}
\right| 
$$
换元之后注意利用对称性。

# 第四题，第五题
![IMG_0626.PNG](https://i.loli.net/2021/10/15/KuAqNtgxXWdfIGS.png)
![IMG_0627.PNG](https://i.loli.net/2021/10/15/MbgfIRrwtyj2Uxv.png)
![IMG_0628.PNG](https://i.loli.net/2021/10/15/GuAFNvBLy3qTmeO.png)
过于巧妙，感觉自己能做到的只有记住傅立叶级数。
- 傅里叶级数
$$
f(x) = \frac{a_0}{2}+\sum_{n=1}^{\infty}[a_n\cos\frac{2\pi n}{T}x+b_n\sin\frac{2\pi n}{T}x] \\\\
a_n = \frac{2}{T}\int_{t_0}^{t_0+T}f(x)\cos\frac{2\pi n}{T}xdx \\\\
b_n = \frac{2}{T}\int_{t_0}^{t_0+T}f(x)\sin\frac{2\pi n}{T}xdx
$$
