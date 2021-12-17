---
title: 数据结构笔记
date: 2021-11-01 11:20:34
tags:
 - 数据结构
comment: 'waline'
---

# 第1章 绪论

## 1.4 算法和算法分析

### 1.4.1 算法
- 一个算法具有下列5个重要特性：
    1. **有穷性**，一个算法必须总是（对任何合法的输入值）在执行有穷步之后结束，且每一步都可在有穷时间（在此，有穷的概念并不是纯数学的，而是在实际上合理的，可接受的）内完成。
    2. **确定性**，算法中的每一条指令必须有确切的含义，读者理解时不会出现二义性。并且在任何条件下，算法只能有唯一的执行路径，即对于相同的输入只能得到相同的输出。
    3. **可行性**，算法中所描述的操作都是通过已实现的基本运算执行有限次来实现的。
    4. **输入**
    5. **输出**

### 1.4.2 算法设计的要求
- 通常设计一个“好”的算法应考虑以下目标：
    1. **正确性**，程序对于**精心选择的典型，苛刻而带有刁难性的**几组输入数据能够得出满足规格说明的结果。（这句话的描述方式让我觉得非常精彩，每次读到它都觉得这本书的写作水平很高）。
    2. **可读性**，算法主要是为了人的阅读与交流，其次才是机器执行。可读性好有助于人对算法的理解；晦涩难懂的程序易于隐藏较多错误，难以调试和被修改。
    3. **健壮性**，当输入数据非法时，算法也能适当地做出反应或进行处理，而不会产生莫名其妙的输出结果。
    4. **效率与低存储量需求**，效率指的是算法执行的时间，存储量指的是算法执行过程中所需要的最大存储空间。

### 1.4.3 算法效率的度量
- **时间复杂度**，是什么怎么算就不多说了，离散上学期也有讲。但需要会算具体语句的**频数**。比如下面代码中`a[i,j]=1;`被执行了多少次。
```C
    for (i = 3; i < n; ++i){
        for (j = 0; j <= 2 * i - 4; ++j){
            a[i, j] = 1;
        }
    }
```
外面的`for`说明里面的循环进行了n-3次，即里面的等差数列共有n-3项。其中第一项为`for(j = 0; j <= 2 * 3 - 4; ++j)`共3次，第二项5次……所以`a[i,j]=1`共被执行了：
$$
    \frac{(3+[3+(n-3-1)\cdot 2])(n-3)}{2}=n^2-4n+3
$$
次。 
- **空间复杂度** 

# 第2章 线性表
- 单链表原地逆置（带头结点） 
思路很简单，边缘情况稍微有些复杂，细节很多。
```C 
void reverse(LinkedList L) 
{ 
    LinkedNode j = L->next, i;
    L->next = NULL;
    while (j){
        i = j->next;
        j->next = L->next;
        L->next = j;
        j = i;
    }
}    
```
待续……

# 第3章 栈和队列

待续……

# 第5章 数组和广义表

## 5.1 数组和线性表的关系以及数组的运算

- 数组的特点：
    1. 可以认为，d维数组的非边界元素具有d个直接前趋和d个直接后继

（数组当然不止这一个特点，但其他的都很明显，不在此列举）

## 5.2 数组的顺序存储结构

- n维数组
![F4A8194BAC16C0B2601EC5DAB7CA0ED0.jpg](https://i.loli.net/2021/11/15/uV27nWlb3N1ZMQ6.jpg)
如果对深度学习有些了解的话，可以把n维数组理解为[张量](https://www.zhihu.com/question/23720923)。
理解了n维数组的本质，再去解决**给定下标计算对应地址**就很简单了。

## 5.3 矩阵的压缩存储

### 5.3.1 对称矩阵

![F216CDB5A6D1A99A7101D9F0D5D9DA57.jpg](https://i.loli.net/2021/11/15/M6WxRswAdqnj7ca.jpg)

### 5.3.2 三角矩阵

![3F519532E08565246B8710E44068C247.jpg](https://i.loli.net/2021/11/15/69isBewjxvopUHO.jpg)

### 5.3.3 带状矩阵

![4B13DF10-1A3F-4006-A499-1A47E98DB0E1.png](https://i.loli.net/2021/11/15/UHki3JtORCQphAL.jpg)

### 5.3.4 随机稀疏矩阵

- **三元组表**
```C
#define MAXSIZE 1000 //设定非零元素最大值
typedef struct  {
    int i, j;
    ElemType e;
}Triple;

typedef struct {
    Triple data[MAXSIZE+1]; //三元组表，data[0]未用
    int mu, nu, tu; //行数、列数、非零元个数
}TSMatrix;
```

- 快速转置
![A5FC6335CEB3FDF2669D5A45E9C8ACCA.jpg](https://i.loli.net/2021/11/15/s3aER8FdMuvGKkt.jpg)
其中的num只需要遍历一次三元组表就可以得到，cpot可以通过num计算得到，所以时间复杂度是$o(n+t)$。

接下来这两个东西稍微看一下就可
- 行逻辑连接的表
![3F38980CF1792EB233EFBC6AD2A2EC05.jpg](https://i.loli.net/2021/11/15/oj2zWuXMbPy4Nv6.jpg)

- 十字链表
![D16EFD521700CD4D585D38D493374D93.jpg](https://i.loli.net/2021/11/15/NkuT81SdHqhU7Wz.jpg)

## 5.4 广义表

1. 广义表的相关表示方法和术语
![6B6A81B2F0E340A5C638C28AF7102903.jpg](https://i.loli.net/2021/11/15/CVRPjf9Y3nzHeS2.jpg)
注意：表尾无论是什么东西，都要用括号括起来。如果表尾什么都没有，那也要把它括起来()；如果表尾的元素是一个空表，那也要把它括起来(())；如果表尾只有一个元素，那也要把它括起来(a)。

2. 广义表的存储结构
    1. 头尾链表

    ```C
    // ATOM==0:原子；LIST==1：子表
    typedef enum {ATOM, LIST} ElemTag;
    typedef struct GLNode{
        ElemTag  tag;
        union {
            AtomType  atom;
            struct {
                struct GLNode  *hp, *tp;
            }ptr;
        }
    }*GList1;
    ```
    结构体里面套联合再套结构体，要看懂。
    ![7CFB8063D13743F5D06DED4E54946B5D.jpg](https://i.loli.net/2021/11/15/anzZhXm5O8FtpJf.jpg)

    2. 扩展的线性表

    ```C
    // ATOM==0:原子；LIST==1：子表
    typedef enum {ATOM, LIST} ElemTag;
    typedef struct GLNode{
        ElemTag  tag;
        union {
            AtomType  atom;
            struct {
                struct GLNode  *hp;
            }
        }
        struct GLNode  *tp;
    }*GList2;
    ```
    个人认为这种存储方式更符合直觉。
    ![D3E16E0DF91FFB5B9E0C85E19A0A372B.jpg](https://i.loli.net/2021/11/15/hN39cToHlMmjtQX.jpg)

3. 求广义表的深度
    - 思路1：表的深度=表中所有元素的深度的最大值+1
    ```C
    int GListDepth(GList1 L)
    {
        if (!L)
            return 1; //空表
        if (L->tag == ATOM)
            return 0; //单原子
        for (max = 0, pp = L; pp; pp = pp->ptr.tp)
        {
            dep = GListDepth(pp->ptr.hp);
            if (dep > max)
                max = dep;
        }
        return max + 1;
    } //GListDepth
    ```
    注意7-12行，是如何遍历一个头尾链表的。

    - 思路2：表的深度=max(表头的深度+1, 表尾的深度)
    ```C
    int GListDepth(GList1 L)
    {
        if (!L)
            return 1; //空表
        if (L->tag == ATOM)
            return 0; //单原子
        dep1 = GListDepth(L->ptr.hp) + 1;
        dep2 = GListDepth(L->ptr.tp);
        if (dep1 > dep2)
            return dep1;
        else
            return dep2;
    } //GListDepth
    ```
4. 复制广义表
```C
Status CopyGList(GList1 &T, GList1 L)
{
    if (!L)
        T = NULL; //复制空表
    else
    {
        T = (GList1)malloc(sizeof(GLNode));
        if (!T)
            exit(OVERFLOW);
        T->tag = L->tag;
        if (L->tag == ATOM)
            T->atom = L->atom; //复制单原子
        else
        {
            CopyGList(T->ptr.hp, L->ptr.hp);
            CopyGList(T->ptr.tp, L->ptr.tp);
        }
    }
    return OK;
} //CopyGList
```
这个算法又一次体现出了递归的妙处：这个函数似乎并没有显式的写出该如何去创建一个新的子表的步骤，但这却是它自己本身要做的事情。所以在看到15，16行的时候，其实从另一个角度上明白了，一个广义表无论括号是怎么嵌套的，这都属于他的逻辑结构，只有里面有字母表示的元素才是有实际意义的。

# 第6章 树和二叉树

## 6.1 树的结构定义和基本操作

- **结点的层次** 表示该结点在树中的相对位置。根为第一层，其它的结点依次下推；若某结点在第L层上，则其孩子在第L+1层上。
- **堂兄弟** 双亲在同一层的结点互为堂兄弟。
- **树的深(高)度** 树中结点的最大层次。
- **有序树** 树中各结点的子树从左至右是有次序的，不能互换。否则，称为无序树。
- **路径长度** 从树中某结点Ni出发，能够“自上而下地”通过树中结点到达结点Nj，则称Ni到Nj存在一条路径，- 路径长度等于这两个结点之间的分支数。
- **树的路径长度** 从根到每个结点的路径长度之和。
- **森林** 是m(m>0)棵互不相交的树的集合。

## 6.2 二叉树

- 满二叉树和完全二叉树
![0122CE3A1F3616FE25A5E0A8E17D4FB4.jpg](https://i.loli.net/2021/11/16/heTwUHmM5tYKlG6.jpg)
- 二叉树的性质
    1. 二叉树的第i层上至多有$2^{i-1}$($i\geq 1$)个结点。
    2. 深度为k的二叉树至多有$2^{k-1}$个结点($k\geq 1$)。
    3. 对任何一棵二叉树T，如果其终端结点数为$n_0$，度为2的结点数为$n_2$，则$n_0=n_2+1$。
    4. 具有n个结点的完全二叉树的深度为 $\lfloor \log 2n\rfloor +1$。
    5. 一棵具有n个结点的完全二叉树(又称顺序二叉树)，对其结点按层从上至下(每层从左至右)进行1至n的编号，则对任一结点$i$($1\leq i\leq n$)有：
        1. 若$i\gt 1$，则i的双亲是$\lfloor i/2\rfloor$；若$i=1$，则$i$是根，无双亲。
        2. 若$2i\leq n$，则i的左孩子是2i；否则，$i$无左孩子。
        3. 若$2i+1\leq n$，则i的右孩子是$2i+1$；否则，$i$无右孩子。
- 二叉树的存储结构
    - 顺序存储
        1. 按照层序存储，遇到空位存0；
        2. 只存存在的节点，但是每个节点要记录它的左右孩子的索引；
        3. 只存存在的节点，但是每个节点要记录它的双亲节点的索引。
    - 链式存储
        1. 二叉链表（左右孩子）
        2. 三叉链表（左右孩子，双亲）

## 6.3 二叉树的遍历

- 目的：非线性结构$\rightarrow$线性结构
- 先序遍历，中序遍历，后序遍历
![3B1FB7A3B106E7BA2B6CCF6E9896D490.jpg](https://i.loli.net/2021/11/16/YuhN2ZesOaM84tW.jpg)
思路比较简单，主要关注思考题部分和代码实现。

- 思考：如何利用两种遍历序列确定一个二叉树
先序序列: ABCDEFGH
中序序列: BDCEAFHG
复原过程如下，务必自己动手画一遍，找一下感觉
![209DEC03C82CD3880E068692BE4B7C8E.jpg](https://i.loli.net/2021/11/16/yD47CTqPWbrf8kj.jpg)

- 算法实现
下面的所有算法都要牢记于脑，内化于心，达到闭上眼睛就能有一张在二叉树上遍历的动图的程度。
    1. 先序遍历
    递归实现
    ```C
    Preorder(BiTree bt)
    {
        if (bt != NULL)
        {
            visite(bt);
            Preorder(bt->lc);
            Preorder(bt->rc);
        }
    }
    ```
    改进的递归算法
    ```C
    Preorder2(BiTree bt)
    {
        visite(bt);
        if (bt->lc != NULL)
        {
            Preorder2(bt->lc);
        }
        if (bt->rc != NULL)
        {
            Preorder2(bt->rc);
        }
    }
    ```
    消除尾递归的算法
    ```C
    Preorder3(BiTree bt)
    {
        while (bt != NULL)
        {
            visite(bt);
            Preorder3(bt->lc);
            bt = bt->rc;
        }
    }
    ```
        **非递归算法**
    ```C
    Preorder4(Bitree bt)
    {
        inistack(s);
        p = bt;
        push(s, NULL);
        while (p != NULL)
        {
            visite(p);
            if (p->rc != NULL)
            {
                push(s, p->rc);
            }
            if (p->lc != NULL)
                p = p->lc;
            else
                p = pop(s);
        }
    }
    ```
    先在栈里铺垫一个NULL
    然后每次循环过来，先visit自己
    然后如果自己的右支不是NULL就入栈
    然后如果自己的左支不是NULL就变成自己的左支；如果自己的左支是NULL就变成出栈元素
    直到自己变成NULL。
    2. 中序遍历
    ```C
    Inorder(BiTree bt)
    {
        if (bt != NULL)
        {
            Inorder(bt->lc);
            visite(bt);
            Inorder(bt->rc);
        }
    }
    ```
    3. 后序遍历
    ```C
    Postorder(BiTree bt)
    {
        if (bt != NULL)
        {
            Postorder(bt->lc);
            Postorder(bt->rc);
            visite(bt);
        }
    }
    ```
    4. 层序遍历
    类似广度优先搜索
    ```C
    Levelorder(BiTreptr bt)
    {
        iniqueue(q);
        if (bt != NULL)
            enqueue(q, bt);
        while (!empty(q))
        {
            t = dequeue(q);
            visite(t);
            if (t->lc != NULL)
                enqueue(q, t->lc);
            if (t->rc != NULL)
                enqueue(q, t->rc);
        }
    }
    ```

## 6.4 线索二叉树

- 通过前面介绍的二叉树可知，遍历二叉树实际上就是将树中所有结点排成一个线性序列（即非线性结构线性化）。在这样的线性序列中，很容易求得某个结点在某种遍历下的直接前趋和后继。然而，有时我们希望不进行遍历，就能很快找到某个结点在某种遍历下的直接前趋和后继。这样，就应该把每个结点的直接前趋和直接后继记录下来。
- 线索二叉树的存储结构
![4C48FA1CD4C00473547C71A4E30EFEF6.jpg](https://i.loli.net/2021/11/16/TQ6dmfYxPpLaW5t.jpg)
![562C5844BA89626B95297A9CDCC5B5FC.jpg](https://i.loli.net/2021/11/16/8EprLsSmIGkgtuz.jpg)
- 但有些结点的Lchild或Rchild指针域指向其左孩子或右孩子，而没有记录其前趋或后继结点信息，要找到该结点的前趋或后继，还要进行一定的搜索。例如，上图A结点的前趋是D（即A结点的左子树的最右下结点）；A结点的后继是F（即A结点的右子树的最左下结点）。那我们该怎么找一个节点的前驱或者后继呢（以中序线索树为例）？
    - 后继
        1. 若p->rtag=1，则p->rc即为所求；
        2. 若p->rtag=0，则从其右子沿着左链走到ltag=1的那个结点就是。
    - 前驱
        1. 若p->ltag=1，则p->lc即为所求；
        2. 若p->ltag=0，则从其左子沿着右链走到rtag=1的那个结点就是。
- 二叉树的中序线索化
```C
pre = NULL;
inthread(BiThrNode p)
{
    if (p != NULL)
    {
        inthread(p->lc);
        if (p->lc == NULL)
        {
            p->ltag = 1;
            p->lc = pre;
        }
        if (pre != NULL)
        {
            if (pre->rc == NULL)
            {
                pre->rtag = 1;
                pre->rc = p;
            }
            pre = p;
            inthread(p->rc);
        }
    }
}
```
先把自己的左支线索化
再把自己线索化，线索化自己的时候，看自己有没有左支，要是没有左支就和pre连起来；再看pre有没有右支，要是没有右支，就和自己连起来，然后每次更新一个都要把pre变成自己。
然后再线索化自己的右支。
其中pre是全局变量。

- 遍历中序线索树
```C
inorder_thlinked(BiThrTree bt)
{
    p = bt;
    while (p != NULL)
    {
        while ((p->ltag == 0)&&(p->lc != NULL))
        {
            p = p->lc;
            visite(p);
            while ((p->rtag = 1) && (p->rc != NULL))
            {
                p = p->rc;
                visite(p);
            }
            p = p->rc;
        }
    }
}
```
要中序遍历一个树，一开始肯定先找他的最左下的结点。找到之后visit他，然后再找他的线索，有没有直接指示的后继，有指示的后继就一路visit过去，直到没有的时候，说明当前的树的左支和自己已经visit完了，可以visit它的右支了，就把自己变成自己的右支，然后visit下一轮。

- 在线索二叉树里更新节点
    自己讨论各种情况寻找一下规律即可，老师也没有讲具体的算法，以下随便举一例：
    在中序线索树中插入结点t，使其称为结点s的右孩子。
    1. 若s无右孩子
        1. s的后继变成t的后继
        2. s成为t的前驱
        3. t成为s的右孩子
    2. 若s有右孩子
        1. s的右孩子变成t的右孩子
        2. s的右孩子的前驱变成t
        3. t的前驱成为s
        4. t变成s的右孩子
    要做几次操作，操作什么顺序，现场要想清楚。

## 6.5 哈夫曼树及其应用

### 6.5.1 术语

![35018878D5742301764187346F76F44F.jpg](https://i.loli.net/2021/11/16/awy7TSIfdPDUjX3.jpg)

### 6.5.2 建立最优二叉树的方法

1. 将给定权值从小到大排序成${w_1,w_2,\cdots,w_m}$，生成一个森林$F={T_1,T_2,\cdots,T_m}$，其中$T_i$是一个带权$W_i$的根结点，它的左右子树均空。
2. 把F中根的权值最小的两棵二叉树T1和T2合并成一棵新的二叉树T：T的左子树是T1，右子树是T2，T的根的权值是T1、T2树根结点权值之和。
3. 将T按权值大小加入F中，同时从F中删去T1和T2
4. 重复2.和3. ，直到F中只含一棵树为止，该树即为所求。
![60A77ACE9A08C129D70983EEEB653890.jpg](https://i.loli.net/2021/11/16/lO9NUXiJBcTqopn.jpg)

### 6.5.3 哈夫曼树的存储结构

```C
Const m = 结点数目；(m = 2n - 1) 
typedef struct
{
    unsigned int weight;
    unsigned int parent, lch, rch;
} HTNode;

Typedef HTNode HuffmanTree[m];

HuffmanTree ht;
```

每个节点存自己的权值，左子右子和双亲。顺序存储。

### 6.5.4 哈夫曼树的应用

- 哈夫曼编码
![E93F171F9274BDDBD41103BE83B1D53A.jpg](https://i.loli.net/2021/11/16/XZzMBP74in5kbju.jpg)

- 哈夫曼编码的特点
    1. 哈夫曼编码是不等长编码
    2. **哈夫曼编码是前缀编码，即任一字符的编码都不是另一字符编码的前缀**
    3. 哈夫曼编码树中没有度为1的结点。若叶子结点的个数为n，则哈夫曼编码树的结点总数为 2n-1
    4. 发送过程：根据由哈夫曼树得到的编码表送出字符数据
    5. 接收过程：按左0、右1的规定，从根结点走到一个叶结点，完成一个字符的译码。反复此过程，直到接收数据结束
