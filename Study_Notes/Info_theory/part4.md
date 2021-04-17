<head>
<script>
(function () {
    var mathconfig = document.createElement("script");
    mathconfig.type = "text/x-mathjax-config";
    mathconfig.text = [
        "MathJax.Hub.Config({",
            "extensions: ['tex2jax.js'],",
            "jax: ['input/TeX', 'output/HTML-CSS'],",
            "tex2jax: {",
                "inlineMath: [ ['$','$'], ['\\\\(','\\\\)'] ],",
                "displayMath: [ ['$$','$$'], ['\\\\[','\\\\]'] ],",
                "processEscapes: true",
            "},",
            "'HTML-CSS': { availableFonts: ['TeX'] }",
        "});"
    ].join("\n");
    var mathparent = (document.head || document.body || document.documentElement);
    mathparent.appendChild(mathconfig);
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = "http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
    var parent = (document.head || document.body || document.documentElement);
    parent.appendChild(script);
})();
</script>
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

另一种 **randomized** decision rule 则使用概率分布 $\hat{\delta}(x)=P(\delta=1|X=x) $， 是拒绝$H_0$的概率！

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

### Neyman-Pearson forumulation
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

## Optimal solution: Bayesian formulation
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