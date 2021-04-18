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