<head>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script>
</head>

# Part IV 信息推断

## Hypothesis test

### Decision Rule

$$
H_0: X\sim p_0(x)\\
H_1: X\sim p_1(x)\\
$$

使用一个 **deterministic** decision rule 进行决策： $\delta: \mathcal{X} \to \{0, 1\}$

$$
\begin{aligned}
\delta(x)&= 1, x\in \mathcal{X}_1\\
&= 0, x\in \mathcal{X}\backslash\mathcal{X}_1=\mathcal{X}_1^c\\
\end{aligned}
$$

当 $\delta(x) = 1$ 时，可认为拒绝原假设 $H_0$，反之亦然。 $\delta(\cdot)$ 被当作假设检验的决策函数使用！

另一种 **randomized** decision rule 则使用概率分布 $\hat{\delta}(x)=P(\delta=1\|X=x) $， 是拒绝$H_0$的概率！

### Bayesian formulation
首先考虑两种假设的先验分布
$$
\begin{aligned}
\pi_0 &= P(X\sim p_0)\\
\pi_1 = 1-\pi_0 &= P(X\sim p_1)
\end{aligned}
$$

然后考虑**决策损失**$C_{i,j}$，即当正确假设为$H_j$时，接受假设$H_i$的损失(包含$i=j$的情况)。则定义真假设$H_j$的条件损失为

$$
R_j(\delta) = C_{1,j}p_j(\mathcal{X}_1) + C_{0,j}p_j(\mathcal{X}_1^c)
$$

注意：每一个假设$H_j$都有一个它自己的条件损失！

则**Bayes risk**定义为

$$
r(\delta) = \pi_0 R_0(\delta) + \pi_1 R_1(\delta)
$$

\# $\mathcal{X}_1 \to \delta \to R_j \to r$

对于 randomized dicision rule 的情况，注意到

$$
\begin{aligned}
& \sum_{x\in\mathcal{X}}\hat{\delta}(x)p_j(x)\\
=& \sum_{x\in\mathcal{X}}P(\delta = 1\|X = x)P(X = x\|H_j)\\
=& p_j(\delta = 1)
\end{aligned}
$$

\# 参照 Neyman-Pearson 中，第I类错误与检验功效的定义

$$
R_j(\hat{\delta}) = C_{1,j}\sum_{x\in\mathcal{X}}\hat{\delta}(x)p_j(x) + C_{0,j}\sum_{x\in\mathcal{X}}\left[ 1 - \hat{\delta}(x)\right]p_j(x)
$$

$$
r(\hat{\delta}) = \pi_0 R_0(\hat{\delta}) + \pi_1 R_1(\hat{\delta})
$$

### Neyman-Pearson formulation
* 与 Bayesian formulation 平行关系
* 不考虑两种假设的香烟分布，也不考虑任何决策损失
* 关注两类错误
 
  |True\Decision|$H_0$|$H_1$|
  |:---|:---|:---|
  |$H_0$| \ | Type I |
  |$H_1$| Type II | \ |

  * $P(\text{Type I error}) = P_F(\hat{\delta})$
  * $P(\text{Type II error}) = P_M(\hat{\delta})$
    * "Power of test" $P_D(\hat{\delta}) = 1 - P_M(\hat{\delta})$ 
* Neyman-Pearson 的设计准则决定于以下的最优化问题(确保第一类错误概率小于置信度$\alpha$的前提下，最大化检验的功效=最小化第二类错误概率)

$$
\max_{\hat{\delta}} P_D(\hat{\delta}),\\
\text{s.t. }P_F(\hat{\delta})\leq \alpha
$$

  注意到

$$
\begin{aligned}
P_F(\hat{\delta}) &= p_0(\delta = 1)\text{, 对 x 用全概率公式展开}\\
&= \sum_{x\in\mathcal{X}}\hat{\delta}(x)p_0(x)\\
P_D(\hat{\delta}) &= p_1(\delta = 1)\\
&= \sum_{x\in\mathcal{X}}\hat{\delta}(x)p_1(x)
\end{aligned}
$$

  它们都与 $\hat{\delta}(x)$ 成线性关系

## Optimal solution

* 问题：根据上文给出的两种formulation，怎样寻找最优的$\delta$决策规则？
* 换言之，怎样寻找 $x\in\mathcal{X}$ 的决策边界 $\mathcal{X}_1$

### Optimal solution: Bayesian formulation
先考虑 deterministic decision rules 的情况

$$
\begin{aligned}
&r(\delta)\\
=& \text{Const} + \sum_{x\in\mathcal{X}_1}[\pi_{0}(C_{1,0}-C_{0,0})p_0(x) + \pi_{1}(C_{1,1}-C_{0,1})p_1(x) ]\\
\end{aligned}
$$

因此最优的$\delta$需要满足

$$
\pi_{0}(C_{1,0}-C_{0,0})p_0(x) + \pi_{1}(C_{1,1}-C_{0,1})p_1(x) \leq 0\text{ if }x\in\mathcal{X}_1\text{ and }>0\text{ otherwise}
$$

这类决策规则被称为似然比检验(likelihood ratio test)，其定义为

$$
L(x) = \frac{p_1(x)}{p_0(x)},x\in\mathcal{X}
$$

因此最优的 $\delta$ 对应的 $\mathcal{X}_1$ 为

$$
\mathcal{X}_1 = \left\{ x\in \mathcal{X}: \frac{p_1(x)}{p_0(x)}\geq\frac{\pi_0}{\pi_1} \right\}
$$

### Optimal solution: Neyman-Pearson formulation
* 此准则下的最优$\delta(x)$是上文最优化问题的最优解！
* The optimal solution under the Neyman-Pearson formulation is given by the following fundamental lemma:
* Neyman-Pearson Lemma: For the Neyman-Pearson design criterion, we have
  * The following decision rule is optimal:
  * 
$$
\begin{aligned}
\hat{\delta}(x)&= 1 \text{ if } L(x)>\eta\\
&= 0 \text{ if } L(x)<\eta\\
&= \gamma(x) \text{ if } L(x) = \eta\\
\end{aligned}
$$

here $\gamma(x) \in [0,1]$ and $\eta \geq 0$are chose **such that** $P_F(\hat{\delta}) = \alpha$

* For every $\alpha\in(0,1)$ the said optimal decision rule exists. and we can always set $\gamma(x) = \gamma_0$ as a constant.
  
### Asymptotic behavior of likelihood ratio

* 似然比检验在Bayesian和Neyman-Pearson formulations 中都扮演中心角色。通常，似然比检验的决策边界为

$$
L(x) = \frac{p_1(x)}{p_0(x)} <> \tau
$$

其中 $\tau > 0$ 是一个精确计算出的决策阈值！

现在考虑随机向量 $\underline{X} = (X_1,\ldots,X_n), X_i\sim i.i.d\,p_0\text{ or }p_1$，则似然比定义为

$$
\begin{aligned}
L(\underline{x}) &= \frac{p_1(\underline{x})}{p_0(\underline{x})} \\
&= \frac{p_1(x_1,\ldots,x_n)}{p_0(x_1,\ldots,x_n)} \\
&= \prod_{i=1}^{n}\frac{p_1(x_i)}{p_0(x_i)}
\end{aligned}
$$

取对数+正则化之后，有

$$
\frac{1}{n}\log L(x) = \frac{1}{n}\sum_{i=1}^{n}\log \frac{p_1(x_i)}{p_0(x_i)}
$$

* 在 $H_0$ 成立时， 
$$ \frac{1}{n}\log L(x)\to E_0 \log \frac{p_1(x_i)}{p_0(x_i)} \to -D(p_0\|p_1)$$
* 在 $H_1$ 成立时， 
$$ \frac{1}{n}\log L(x)\to E_1 \log \frac{p_1(x_i)}{p_0(x_i)} \to D(p_1\|p_0)$$

**因此，当 $n\to\infty$ 时，似然比检验能以任意精度区分开 $H_0$ 和 $H_1$ !**

to be continued...
to be continued...