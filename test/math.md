---
title: 6_多元函数积分学
index_img: /post_index_img/maths.png
date: 2020-02-03 11:11:16
categories:
    - 考研
    - 数学
    - 数学
---

# 1. 重积分

- 二重积分
    $$
    \iint_{D}^{}f(x,y)d\sigma\overset{\Delta }{=}\lim_{d\rightarrow 0} \sum_{k=1}^{n}f(\xi_{k},\eta_{k})\Delta \sigma_{k}
    $$
    $d:n个小区域直径的最大值~~~~\Delta \sigma_{k}:\ 第k个小区域的面积$  
    $f连续,积分总存在$
    - $f非负\rightarrow圆顶柱体体积$
- 性质
  - 比较定理 $::~~~f\leqslant g\Rightarrow \iint_{D}^{}f(x,y)d\sigma\leqslant \iint_{D}^{}g(x,y)d\sigma$
  - 估值定理 $::~~~\rightsquigarrow\land S::D的面积\Rightarrow mS\leqslant \iint_{D}^{}f(x,y)d\sigma\leqslant MS$
  - 中值定理 $::~~~\rightsquigarrow\Rightarrow 至少一点\iint_{D}^{}f(x,y)d\sigma=f(\xi,\eta)S$
- 计算
  - 直角坐标系
    - $先y后x::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{a}^{b}dx\int_{\varphi_{1}(x)}^{\varphi_{2}(x)}f(x,y)dy$
    - $先x后y::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{c}^{d}dy\int_{\varphi_{1}(y)}^{\varphi_{2}(y)}f(x,y)dx$
  - 极坐标
    - $O在D之外::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{\alpha }^{\beta }d\theta \int_{\rho_{1} (\theta )}^{\rho _{2}(\theta )}f(\rho \cos \theta ,\rho \sin \theta )\rho d\rho$
        <center> <img src="6_%E5%A4%9A%E5%85%83%E5%87%BD%E6%95%B0%E7%A7%AF%E5%88%86%E5%AD%A6/2020-08-09-22-41-16.png" width="150px"/> </center>

    - $O在D的边界上::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{\alpha }^{\beta }d\theta \int_{0}^{\rho (\theta )}f(\rho \cos \theta ,\rho \sin \theta )\rho d\rho$
        <center> <img src="6_%E5%A4%9A%E5%85%83%E5%87%BD%E6%95%B0%E7%A7%AF%E5%88%86%E5%AD%A6/2020-08-09-22-40-38.png" width="150px"/> </center>

    - $O在D的内部::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{0}^{2\pi}d\theta \int_{0}^{\rho (\theta )}f(\rho \cos\theta ,\rho \sin\theta )\rho d\rho$
        <center><img src="6_%E5%A4%9A%E5%85%83%E5%87%BD%E6%95%B0%E7%A7%AF%E5%88%86%E5%AD%A6/2020-08-09-22-38-53.png" width="150px"/></center>

    - $O在环形域的内部::~~~\iint_{D}^{}f(x,y)d\sigma=\int_{0}^{2\pi}d\theta \int_{\rho _{1}(\theta )}^{tho_{2}(\theta )}f(\rho \cos\theta ,\rho \sin\theta )\rho d\rho$
        <center> <img src="6_%E5%A4%9A%E5%85%83%E5%87%BD%E6%95%B0%E7%A7%AF%E5%88%86%E5%AD%A6/2020-08-09-22-39-53.png" width="150px"/> </center>
        
- 利用对称性和奇偶性
  - 关于xy轴对称
  - 利用变量的对称性  
    $D关于x=y对称$
    $$\iint_{D}^{}f(x,y)d\sigma=\iint_{D}^{}f(y,x)d\sigma$$

---
- 计算
  - 对称性,奇偶性
    - $对y奇函数\xrightarrow[]{积分域x对称}$
    - $xyf(x^2+y^2)\rightarrow 对x,y对称$
      - <img src="6_%E5%A4%9A%E5%85%83%E5%87%BD%E6%95%B0%E7%A7%AF%E5%88%86%E5%AD%A6/2020-08-09-22-14-21.png" width="200px"/>
      - $=0$
    - $Dy=x对称$
      - $\iint_{D}^{}x=\iint_{}^{}y\Rightarrow \iint_{}^{}(x+y)=2\iint_{}^{}x\Rightarrow形心公式$
      - $\int_{}^{}xdx=\int_{}^{}ydy$
    - 极坐标圆心不在原点
      - $(x-a)^2+(y-b)^2=c^2\Rightarrow \begin{cases} x-a=\rho\cos\theta \\y-b=\rho\sin\theta \end{cases}~~d\sigma=\rho d\rho d\theta$
    - $\int_{0}^{2\pi}\cos\theta||\sin\theta =0$
    - 变量代换
      - $\underbrace{(x-a)^2}_{X^2}+\underbrace{(y-b)^2}_{Y^2}=c^2\xrightarrow[]{积分域y=b对称}\iint_{}^{}\underbrace{(x-a)}_{X}d\underbrace{x}_{X}=0\xrightarrow[]{积分域x=a对称\rightarrow y同理}\iint_{}^{}x+y=\iint_{}^{}\underbrace{(x-a)}_{=0}+\underbrace{(y-a)}_{=0}+2a=\iint_{}^{}2a\mathrm{d}\sigma$
      - $\xrightarrow[]{积分域y=1对称}\iint_{}^{}y-1=0\Rightarrow \iint_{}^{}y=\iint_{}^{}(y-1)+1=\iint_{}^{}1=面积$
  - 形心公式
    - $\bar{x}=\frac{\iint_{D}^{}xd\sigma}{\iint_{D}^{}d\sigma}$
    - $\xrightarrow[]{积分域y=1对称}\bar{y}=1\rightarrow\iint_{}^{}y=\bar{y}\cdot面积$
  - 参数方程
    - 先用 x,y 积,再换成t
      - $\begin{cases} x=a(t) \\ y=b(t) \end{cases}\rightarrow \iint_{}^{}y^2=\int_{m}^{n}dx\int_{0}^{y}y^2=\int_{m}^{n}y^3dx\rightarrow在换成t$
  - 被积函数分段
    - $求出被积函数\xrightarrow[]{范围就是积分域}$
  - 被积函数绝对值
    - 去绝对值
      - 被积函数是个圆$\rightarrow$圆内<0,圆外>0
  - $\min\{x,y\}$
    - $y=x划分为两个区域 \iint_{D_1}^{}x+\iint_{D_2}^{}y$
  - 累次积分
    - 极坐标下化为累次积分
  - 函数中有积分值
    - $f(x,y)=\varphi(x,y)-\iint_{}^{}f(u,v)$
      - 设积分值为A
        - $\underbrace{\iint_{}^{}f(u,v)}_{A}=\iint_{}^{}(\varphi-\underbrace{\iint_{}^{}f(u,v)}_{A})\rightarrow A$
      - 两端积分
        - $\iint_{}^{}f(x,y)=\iint_{}^{}\varphi+S\cdot \iint_{}^{}f(u,v)\xrightarrow[]{\iint_{}^{}f(x,y)=\iint_{}^{}f(u,v)}$
    - $f(t)=Q(t)+\iint_{}^{}f(\varphi(x,y))dxdy$
      - 判断可能的$f$值
        - $D:x^2+y^2\leqslant t^2\xrightarrow[]{t=0}f(t)=\varphi(t)$
      - $\iint_{}^{}f(\varphi(x,y))=A\int_{\psi_1(t)}^{\psi_2(t)}m(\rho)f(\rho)d\rho\xrightarrow[]{代回}f(t)=Q(t)+A\int_{\psi_1(t)}^{\psi_2(t)}m(\rho)f(\rho)d\rho\xrightarrow[]{求导}f'(t)=Q'(t)+n(t)f(t)\xrightarrow[]{一阶线性微分方程通解}$
  - 极限
    - ${ \atop x \rightarrow 0}\frac{\int_{0}^{x^2}dt\int_{x}^{\sqrt[]{t}}f(t,u)du}{{ \atop \rightarrow 0}}$
      - $分子求导\int_{x}^{x}??\xrightarrow[]{换序}\frac{-\int_{0}^{x}du\int_{0}^{u^2}f(t,u)dt}{{ \atop   \rightarrow 0}}\xrightarrow[]{洛必达}-\frac{\int_{0}^{x^2}f(t,x)dt}{{ \atop   \rightarrow 0}}\xrightarrow[]{积分中值}-\frac{x^2f(c,x)}{{ \atop   \rightarrow 0}}\xrightarrow[]{{ \atop x \rightarrow 0}f(c,x)=f(0,0)}$
    - 积分区域极限到原点 $\iint_{}^{}f(t,u)dtdu=f(\xi,\eta)\cdot S=f(0,0)\cdot S$
      - $\int_{0}^{x^2}dt\int_{x}^{\sqrt[]{t}}f(t,u)du=-\iint_{D}^{}f(t,u)dtdu=-f(\xi,\eta)\cdot S\xrightarrow[]{{ \atop x \rightarrow 0}f(\xi,\eta)=f(0,0)}$
  - $xy换\rho\theta 全导数$
    - $\int_{}^{}\cos\theta f'_{x}(\rho\cos\theta ,\rho\sin\theta )+\sin\theta f'_{y}(\rho\cos\theta ,\rho\sin\theta )=f(\rho\cos\theta ,\rho\sin\theta )$
  - 利用积分中值定理
    - $-\frac{\int_{0}^{x^2}f(t,x)dt}{{ \atop   \rightarrow 0}}\xrightarrow[]{积分中值}-\frac{x^2f(c,x)}{{ \atop   \rightarrow 0}}\xrightarrow[]{{ \atop x \rightarrow 0}f(c,x)=f(0,0)}$
    - $\int_{0}^{a}f(\epsilon\cos\theta ,\epsilon\sin\theta )=2af(\epsilon\cos\bar{\theta },\epsilon\sin\bar{\theta})\xrightarrow[]{{ \atop \epsilon \rightarrow 0}}=2af(0,0)$
- 积分不等式
  - 积分性质比较定理
  - 两个定积分化为重积分
    - 将一个化为 $y$
      - $\int_{}^{}f(x)dx\cdot\int_{}^{}\underbrace{\frac{1}{f(x)}dx}_{\frac{1}{f(y)}dy}=\iint_{D}^{}\frac{f(x)}{f(y)}dxdy)$
    - 柯西积分不等式
      - $\int f(x)\cdot\int \frac{1}{f(x)}\geqslant (\int\sqrt[]{f(x)}\cdot\frac{1}{\sqrt[]{f(x)}})^2=(\int_{}^{}1)^2$
  - 换积分域
    - $D_1:{0\leqslant x\leqslant 1\atop 0\leqslant y\leqslant 1}\rightarrow D_2:x^2+y^2\leqslant 1\rightarrow\iint_{D_1}^{}e^{-(x^2+y^2)}>\int_{D_2}^{}e^{-(x^2+y^2)}\xrightarrow[]{换极坐标}$
  - 麦克劳林展开式 ($x$的幂级数)
    - $\int_{}^{}e^{-x^2}\leqslant \int_{}^{}(1-x^2+\frac{x^{4}}{2!})=A$

## 1.2 三重积分
- 有界 $\iiint_{\Omega}^{}f(x,y,z)dV\overset{\Delta }{=}\lim_{\lambda\rightarrow 0} \sum_{k=1}^{n}f(\xi_{k},\eta_{k},\zeta_{k})\Delta v_{k}$
- 性质
  - 比较定理
  - 估值定理
  - 中值定理  
- 直角坐标
  - 先一后二 $\iint_{\Omega}^{}f(x,y,z)dV=\iint_{D}^{}dxdy\int_{z_{1}(x,y)}^{z_{2}(x,y)}f(x,y,z)dz$
  - 先二后一 $\iint_{\Omega}^{}f(x,y,z)dV=\int_{a}^{b}dz\iint_{D_{z}}^{}f(x,y,z)dxdy$  
    *通常$f(x,y,z)$是$z$的一元函数*
- 柱坐标
  - 柱坐标$(r,\theta ,z)$与直角坐标
    - $\begin{cases} x=r\cos \theta \ ,0\leqslant r\leqslant +\infty \\y=r\sin \theta \ ,0\leqslant \theta \leqslant 2\pi \\z=z\ ,-\leqslant z\leqslant +\infty \end{cases}~~~~ dV=rdrd\theta dz.$  
     $\iint_{\Omega}^{}f(x,y,z)dV=\iint_{\Omega}^{}f(r\cos \theta ,r\sin\theta ,z)rdrd\theta dz$  
     $[一般适用于]::~~~f(x,y,z)=\varphi(z)g(x^2+y^2)$  
      积分域为柱体,锥体,柱面,锥面与其他曲面所围空间等
    - 积分次序: $z,r,\theta||r,\theta ,z$
- 球坐标
    - 球坐标$(r,\varphi,\theta )$与直角坐标
      - $\begin{cases} x=r\sin\varphi\cos\theta \ \ ,0\leqslant r\leqslant +\infty \\y=r\sin\varphi\sin\theta \ \ ,0\leqslant \varphi\leqslant \pi \\z=r\cos\varphi\ \ \ \ ,0\leqslant \theta \leqslant 2\pi \end{cases}~~~~ dV=r^2\sin\varphi dr d\varphi d\theta$  
        $\varphi : r\rightarrow z~~~~ \theta : r\sin\theta \rightarrow x$  
        $\iint_{\Omega}^{}f(x,y,z)dV=\iint_{\Omega}^{}f(r\sin\varphi\cos\theta ,r\sin\varphi\sin\theta ,r\cos\varphi)r^2\sin\varphi drd\varphi d\theta$  
        $[一般适用于]::~~~f(x,y,z)=\varphi (x^2+y^2+z^2)$  
        积分域为球体,半球体,锥面与球面所围空间体等
      - 积分次序: $r,\varphi,\theta$
- 对称性和奇偶性
  - 积分域的对称性和被积函数的奇偶性
  - 变量对称性
    - 若将表示积分域的x和y对调后方程不变,则  
      $\iint_{\Omega}^{}f(x,y,z)dV=\iint_{\Omega}^{}f(y,x,z)dV$

---

- $\iint_{\Omega}^{}zdxdy$
   - $z$ 截的区域是圆, $\Omega::~~~x^2+y^2可用z表示,被积函数只有z$
      - $\iint_{\Omega}^{}z=\int_{}^{}dz\iint_{}^{}zdxdy=\int_{}^{}z\cdot\pi\underbrace{(x^2+y^2)}_{用z表示}$
    - 形心公式
      - $=\bar{z}\cdot V$
    - 对称性,奇偶性
      - $例\Omega z=1对称::~~~\iint_{}^{}zdV=\underbrace{\iint_{}^{}z-1}_{=0}+\iint_{}^{}dV$
- 球坐标对称性
  - $\iint_{}^{}x^2dV=\iint_{}^{}y^2dV=\iint_{}^{}z^2dV$
  - $mx^2+ly^2+nz^2=(m+l+n)x^2=\frac{(m+l+n)}{3}(\underbrace{x^2+y^2+z^2}_{换成r})$
- 累次积分可以提前提出来
  - $\int_{0}^{2\pi}d\theta \int_{}^{}dr\int_{}^{}\varphi(r,z)=2\pi\int_{}^{}dr\int_{}^{}\varphi(r,z)$
- 积分次序
  - 函数中只有z,那就把z换到最后积