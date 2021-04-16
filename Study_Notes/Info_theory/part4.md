<head>
<script type="text/javascript"
src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
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
