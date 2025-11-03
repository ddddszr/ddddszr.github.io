---
title: Euler公式和余元公式
date: 2017-03-05 19:40:00
tags: [分析]
cetegories: Math
mathjax: true

---
像Euler公式这样的优美等式，当然是越早接触越好。余元公式是研究$\Gamma(x)$的产物，也是重要的结论。这里把二者再复述一遍，一是因为它们有一定的内在联系，二是用自己的话说一遍也好加深印象。

---
Euler最先发现，对于$x\in\Bbb R$,$x\neq k\pi(k\in\Bbb Z)$，有如下关系成立：
$$\sin x=x\cdot\prod_{n=1}^{+\infty}\left(\frac{x^2}{1-n^2{\pi}^2}\right).$$
先把它放在这里，转而研究伽马函数：$\Gamma(x)=\int_0^{+\infty}t^{x-1}e^{-t}\Bbb{d}t(x>0)$.它有如下几条重要性质：
* $\forall x>0$,$\Gamma(x)<+\infty$.

proof：这说明对于任一自变量伽马函数不是正无穷大，放在下面证明。
* $\Gamma(x+1)=x\Gamma(x)$,特别的，当$n\in\Bbb N_+$时，$\Gamma(n)=(n-1)!$.

proof:对其分部积分，得到
$$
\Gamma(x+1)=-e^t\cdot t^x\bigg|_0^{+\infty}+x\cdot\int_0^{+\infty}  t^{x-1}e^t\Bbb dt=x\Gamma(x).
$$
又$\Gamma(1)=1$,即证。由此可以看出，$\Gamma(x)$是阶乘在实数域上的延拓，从而又与Stirling公式有联系。
* $\Gamma(\frac12)=\sqrt{\pi}$.

proof：由Euler-Poisson积分以及换元法得到，
$$
\Gamma\left(\frac12\right)=\frac12\int_0^{+\infty}\frac{1}{re^{r^2}}\Bbb dr^2=\int_0^{+\infty}\frac1{e^{r^2}}\Bbb dr=\sqrt{\pi}.
$$
从第三条出发，我们想研究$\Gamma(x)\Gamma(1-x)$的性质。为此，先给出$\Gamma(x)$的另一个定义(无穷乘积)：
对于$x\neq k(k\in\Bbb N)$,定义：
$$
\Gamma(x)=\frac1x\prod_{n=1}^{+\infty}\frac{\left(1+\frac1n\right)^x}{1+\frac xn}.
$$
由$\ln\frac{\left(1+\frac1n\right)^x}{1+\frac xn}$ ~ $\ln\left(1+\frac{x(x-1)}{2n^2}\right)$ ~ $\frac{x(x-1)}{2n^2}(n\to+\infty)$知该无穷乘积收敛，所以$\Gamma(x)$有意义，从而可以证明第一个命题。由：
$$
\prod_{i=1}^{n}\frac{\left(1+\frac1i\right)^x}{1+\frac xi}=\left(\frac{n+1}{n}\right)^x\cdot\frac{n!n^x}{x(x+1)\cdots(x+n)},
$$
就得到Euler-Gauss公式：
$$
\Gamma(x)=\lim_{n\to+\infty}\frac{n!n^x}{x(x+1)\cdots(x+n)}.
$$
继而
$$
\frac{\Gamma(x+1)}{\Gamma(x)}=\lim_{n\to+\infty}\frac{nx}{x+n+1}=x.
$$
通过引入$\gamma$(Euler常数)得到：
$$
e^{\gamma x}=\prod_{n=1}^{+\infty}\frac{e^{\frac xn}}{\left(1+\frac1n\right)^x}.
$$
再结合$\Gamma(x)$的定义就得到Weiestrass公式：
$$
\frac1{\Gamma(x+1)}=e^{\gamma x}\cdot\prod_{n=1}^{+\infty}\left(1+\frac xn\right)e^{-\frac xn}.
$$
利用上边结论得到：
$$
\Gamma(1-x)=(-x)\Gamma(-x)=\prod_{n=1}^{+\infty}\frac{\left(1+\frac1n\right)^{-x}}{1-\frac xn},
$$
结合Weiestrass公式就得到余元公式：
$$
\Gamma(1-x)\Gamma(x)=\frac{\pi}{\sin \pi x}.
$$
令$x=\frac12$就得到$\Gamma(\frac12)=\sqrt{\pi}$.以上是余元公式的推导，下面看余元公式和Euler公式之间有什么关系。

---
Euler公式的推导
设$x\in(0,\pi)$,在余元公式中，令$t=\frac x{\pi}\in(0,1)$,则$\Gamma(1-t)\Gamma(t)=\frac{\pi}{\sin x}$,则$\sin x=\frac{\pi}{\Gamma(1-t)\Gamma(t)}$.根据Gamma函数的无穷乘积定义，
$$
\Gamma\left(\frac x{\pi}\right)=\lim_{n\to+\infty}\frac{\pi\frac x{\pi}(1+\frac x{\pi})\cdots(n+\frac x{\pi})}{n!n^{\frac x{\pi}}}=\lim_{n\to+\infty}x\left(1+\frac x{\pi}\right)\cdots\left(1+\frac x{n\pi}\right).
$$
同理，
$$
\Gamma\left(1-\frac x{\pi}\right)=\lim_{n\to+\infty}\left(1-\frac x{\pi}\right)\cdots\left(1-\frac x{n\pi}\right)
\cdot\frac{n+1-\frac x{\pi}}{n}.
$$
整理，
$$
\sin x=\frac{\pi}{\Gamma(1-\frac x{\pi})\Gamma(\frac x{\pi})}=\lim_{n\to+\infty}x\left(1-\frac {x^2}{\pi^2}\right)\left(1-\frac {x^2}{4\pi^2}\right)\cdots\left(1-\frac {x^2}{n^2\pi^2}\right).
$$
即$x\in(0,\pi)$时，成立，那么当$x\in(-\pi,0)$时由奇偶性易知也成立.
下面讨论一般情况，设$x=2k\pi+y(k\in\Bbb Z,y\in(-\pi,\pi),y\neq0)$,则有
$$
\sin x=\sin y=y\prod_{n=1}^{+\infty}\left(1-\frac{y^2}{n^2{\pi}^2}\right)
$$
只要证明
$$
\prod_{n=1}^{+\infty}\left(1-\frac{y^2}{n^2{\pi}^2}\right)=\frac{2k\pi+y}y\prod_{n=1}^{+\infty}\left(1-\frac{(2k\pi+y)^2}{n^2{\pi}^2}\right).
$$
先考虑k为正整数的情况，记RHS的部分积为$Q_n$，LHS的部分积为$P_n$.
$$
Q_n=\frac{2k\pi+y}y\cdot\prod_{s=1}^{n}\left[\frac{((s+2k)\pi+y)((s-2k)\pi-y)}{s^2\pi^2}\right].①
$$
将$s=1$至$s=2k$的$(s-2k)\pi-y$的负号提出，$Q_n$值不变，即：
$$
Q_n=\frac{2k\pi+y}y\cdot\prod_{s=1}^{2k}\left[\frac{((2k+s)\pi+y)((2k-s)\pi+y)}{s^2\pi^2}\right]\cdot
\frac{Q_n}{Q_{2k}},②
$$
只交换部分项并合并：
$$
Q_n=\prod_{s=1}^{n-2k}\frac{(s\pi+y)(s\pi-y)}{s^2\pi^2}\cdot\prod_{s=n-2k+1}^{n+2k}\frac{(s\pi+y)(s\pi-y)}{s^2\pi^2}.③
$$
③中第一个连乘积是$P_{n-2k}$,右边是分子分母均为$4k$次的多项式且最高次项项系数均为$\pi^{4k}$,所以
$$
\lim_{n\to+\infty}Q_n=\lim_{n\to+\infty}P_n.
$$
当$k< 0$时，只要让$x=-t$，由已知亦可同理证得。
在$\sin x$的无穷乘积展开式中，令$x=\frac {\pi}2$就得到Wallis公式，可知Euler公式是很强力的结论。

---
证明过程是有困难的，沿着前人的路子毕竟好走许多。

---
参考文献：
[1].谢惠民.数学分析习题课讲义(下)，2004
[2].陈纪修.数学分析，2004
[3].朱传汇.《正弦函数sinx的无穷乘积展开式》.襄阳师专学报(自然科学版)，P51.