<head>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script> <script type="text/x-mathjax-config"> MathJax.Hub.Config({ tex2jax: { skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'], inlineMath: [['$','$']] } }); </script>
</head>

# Part III Data Compression

## Definition of data compression codes
* Denote the D-ary codeword alphabet by $\mathcal{D} = \{0,1,\ldots,D-1 \}$
* Define $\mathcal{D}^*$ as the set of finite-length strings of symbols from $\mathcal{D}$.
* A D-ary code $C$ for a R.V. $X$ is a mapping from $\mathcal{X}$ to $\mathcal{D}$
* $C(x)$: codeword corresponding to x
* $l(x)$: length of $C(x)$

\#: Here a codeword is assigned to a source data symble, thus this is a symbol-by-symbol coding framework.

* Definition: Expected length(期望长度). The expected $L(C)$ of a data compression code $C$ for a R.V. $X\sim p(x)$ is given by

$$
L(C) = \sum_{x\in\mathcal{X}}p(x)l(x) = E_{p(x)}l(x)
$$

## Consideration on usable codes
### non-singularity
* Def non-singularity: $x\neq x' \Rightarrow C(x) \neq C(x') $

### unique decodability
* Def extension: The extension $C*$ of a code $C$ is the mapping from finite-length strings of $\mathcal{X}$ to finite-length strings of $\mathcal{D}$, defined by

$$
C(x_1 x_2\ldots x_n) = C(x_1)C(x_2)\ldots C(x_n)
$$

  That is, the concatenation(拼接) of symbol-by-symbol codewords

Def uniquely decodable: A code is called $\sim$ if its **extension** is **nonsingular**

### prefix property
* Def prefix code: A code is called $\sim$ or an instantaneous code if **no codeword is a prefix of any othr codeword.**

All codes > Nonsingular > Uniquely decodable > Prefix

* Property: A code $C$ is uniquely decodable if and only if 

$$
C^k(x_1,\ldots,x_n) = C(x_1),\ldots,C(x_k)
$$

is a one-to-one mapping from $\mathcal{X}^k$ to $\mathcal{D}^*$ for every $k\geq 1$

## Kraft inequality for prefix codes
* $D$: the size of the D-ary codeword alphabet
* $l(x)$: length of $C(x)$
* Theorem Kraft inequality:

$$
\sum_{x\in\mathcal{X}}D^{-l(x)}\leq 1
$$

## Kraft inequality for uniquely decodable codes
* Theorem: For any uniquely decodable code, the codword lengths must satisfy the Kraft inequality, and the converse also holds.


## Minimum expected length of codes
* consider the constrained optimization problem:

$$
\min_{l_i, i=1,\ldots,|\mathcal{X}|}\sum_{i}p_i l_i\\
\text{s.t.}\quad \sum_{i}D^{-l_i}\leq 1\\
\forall l_i\geq 1 \text{ integer}
$$

It can be proofed that 

$$
0 \leq D(p\|q)\leq -H(X) + \sum_{i}p_i l_i
$$

Thus we need to choose $\left\{ l_i \right\}$ such that

$$
p_i = D^{-l_i},\text{i.e.}, l_i = \log_D\frac{1}{p_i},\quad i=1,\ldots,|\mathcal{X}|
$$




To be continued...