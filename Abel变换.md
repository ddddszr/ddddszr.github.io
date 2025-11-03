---
title: Abel变换及浅显应用(防遗忘)
date: 2017-02-21 12:32:00
tags: [分析]
categories: Math
mathjax: true

---
Abel变换：对于数列$\{a_n\}$、$\{b_n\}$，已知$\sum_{i=1}^k a_k=S_k$,则有如下变换：
$$
\sum_{i=1}^na_ib_i=\sum_{i=1}^{n-1}S_i\cdot(b_i-b_{i+1})+S_nb_n.
$$
从形式上看，好像是对$\{b_n\}$作差分，最后再补上$S_nb_n$(其实对$\{a_n\}$也一样)。下面证明之。
proof：定义$S_0=0.$
$$
\begin{align*}
\sum_{i=1}^na_ib_i&=\sum_{i=1}^n(S_{i}-S_{i-1})\cdot b_i=\sum_{i=1}^nS_ib_i-\sum_{i=1}^nS_{i-1}b_i\\
&=\sum_{i=1}^nS_ib_i-\sum_{i=0}^{n-1}S_ib_{i+1}=S_nb_n-S_0b_1+\sum_{i=1}^{n-1}S_i(b_i-b_{i+1})\\
&=\sum_{i=1}^{n-1}S_i\cdot(b_i-b_{i+1})+S_nb_n\\
&=S_nb_n-\sum_{i=1}^{n-1}S_i\cdot(b_{i+1}-b_{i}).
\end{align*}
$$
我们发现，其本质不过是把$a_k$表示成$S_k-S_{k-1}$，但是经过这个变换，把两个数列对应项乘积和和$S_n$联系了起来。而且最后一个式子很像分部积分，只不过是离散形式($dx$就是那个$b_n-b_{n+1}$的差分)——不知道Abel当时发现它时是不是受到了分部积分的启发。

Abel引理：设$\{a_n\}$为单调数列，定义$B_k=\sum_{i=1}^kb_k$,若$B_n$有界，即$\forall n,|B_n|\le M$，则：
$$
\left|\sum_{k=1}^p a_kb_k\right|\le M(|a_1|+2|a_p|).
$$
proof:这是一个著名引理，用于证明A-D判别法。由Abel变换得：
$$
\begin{align*}
\left|\sum_{k=1}^p a_kb_k\right|&\le|a_pB_p|+\sum_{i=1}^{p-1}|a_{k+1}-a_k|\cdot|B_k|\\
&\le M\left(|a_p|+\sum_{k=1}^{p-1}|a_{k+1}-a_{k}\right)①.
\end{align*}
$$
由于$a_n$单调，所以
$$
\sum_{k=1}^{p-1}|a_{k+1}-a_{k}|=\left|\sum_{k=1}^{p-1}(a_{k+1}-a_{k})\right|=|a_p-a_1|,
$$
将上式代入①即得结论。

---
先看一个简单应用：正项数列$\{a_n\}$、$\{b_n\}$的无穷和都收敛，证明$\sum a_nb_n$也收敛。
proof：由Abel变换，
$$
\sum a_nb_n=\sum S_i(b_i-b_{i+1})+S_{+\infty}\cdot b_{+\infty}\\
=\sum S_i(b_i-b_{i-1})\\
<\sum S_i(b_i+b_{i+1})\\
=\sum_{i=1}^{N}S_i(b_i+b_{i+1})+\left(\sum_{i=N+1}^{+\infty}S_i(b_i+b_{i+1})\right)\\
<\sum_{i=1}^{N}S_i(b_i+b_{i+1})+\left((S+1)\cdot\sum_{i=N+1}^{+\infty}(b_i+b_{i+1})\right)\\
\le 2S(S+1)+K.(K=constant)
$$
或许有简单方法，不过看见乘积我就直接Abel了。从这里可以看出因为$\{b_n\}$不是单调的，所以我必须花一些力气去放缩使它变成单增的(放成$\{b_n+b_{n+1}\}$)，这也提醒了我们最好选择单调的那个数列作为差分项。(原谅我没冲齐等号，因为hexo抽了，其他的都好好的就这个用align命令爆炸)

eg2.已知正项级数$\sum a_n$收敛，证明$\frac1n\sum_{i=1}^nka_k\to0.$
proof:由上一题经验，我们把$\{n\}$作为差分项，记$\sum_{i=1}^ka_k=S_k$,用Abel变换：
$$
\frac1n\sum_{i=1}^nka_k=\frac1n\left(nS_n-\sum_{i=1}^{n-1}\sum_{j=1}^ia_j\right)=S_n-\frac1n\sum_{i=1}^{n-1}S_{i}.
$$
由Cauchy命题，$\frac1n\sum_{i=1}^{n-1}S_{i}\to\lim S_n=S$,即证。

eg3(IMO-20).已知$a_i\in\Bbb N^+$,$a_i\neq a_j(i,j\in\Bbb N^+)$.证明对任一正整数n，有：
$$
\sum_{i=1}^n\frac{a_k}{k^2}\ge\sum_{i=1}^n\frac1k.
$$
proof1:这个题很简单，用Cauchy不等式
$$
\sum_{i=1}^n\frac{a_k}{k^2}\ge\left(\sum_{i=1}^n\frac1k\right)^2\cdot\left(\sum_{i=1}^n\frac 1{a_k}\right)^{-1}\ge\sum_{i=1}^n\frac1k.
$$
一行就解决了(因为$a_i$各不相等)。
proof2：但我还是要用Abel做一下，不然怎么能凑够三个题呢(笑)。记$S_k=a_1+\cdots+a_k.$
$$
\begin{align*}
\sum_{i=1}^n\frac{a_k}{k^2}&=\frac1{n^2}S_n+\sum_{i=1}^{n-1}S_i(\frac1{i^2}-\frac1{(i+1)^2})\\
&\ge\frac1{n^2}\cdot\frac{n(n+1)}2+\sum_{i=1}^{n-1}\frac{i(i+1)}2(\frac1{i^2}-\frac1{(i+1)^2})\\
&=\frac{n+1}{2n}+\sum_{i=1}^{n-1}\frac{2i+1}{2i(i+1)}\\
&=\frac{n+1}{2n}+\frac12\sum_{i=1}^{n-1}\frac1{i(i+1)}+\sum_{i=1}^{n-1}\frac1{i+1}\\
&=\frac12+\frac12+\frac1n+\sum_{i=1}^{n-1}\frac1{i+1}=\sum_{i=1}^n\frac1i.
\end{align*}
$$
可以看出就是无脑化简，只是写起来麻烦些。

---
更麻烦的Abel变换的应用大概在填坑到级数时会详细说，今天只是为了复习一下。

又，周期三蕴含混沌的四个习题没做，5.2的第10题也没做出来。
