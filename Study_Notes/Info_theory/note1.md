# HW2
## ex4
试证明对于 R.V. $X,\alpha\in R$, $f(x)$ 为定义在实数域上的任意函数，有
$$
H(X) \leq \alpha Ef(X) + \ln\sum_{u\in\mathcal{X}}e^{-\alpha f(u)}
$$
proof. 
$$
\begin{aligned}
& \alpha Ef(X) + \ln\sum_{u\in\mathcal{X}}e^{-\alpha f(u)} - H(X)\\
=& \sum_{x\in\mathcal{X}}p(x)\left[\alpha f(x)  + \ln\sum_{u\in\mathcal{X}}e^{-\alpha f(u)} + \ln p(x) \right]\\
=& \sum_{x\in\mathcal{X}}p(x)\ln\left\{ \frac{p(x)}{e^{-\alpha f(x)}/\sum_{u\in\mathcal{X}}e^{-\alpha f(u)}} \right\}\\
=& D(p(x)\|q(x)) \geq 0
\end{aligned}
$$