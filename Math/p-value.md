---
tags: #definition
---

  
**Definition:** Let [null hypothesis](/D/h0) be $H_0$ and the [alternative hypothesis](/D/h1) $H_1$ using the [test statistic](/D/tstat) $T(Y)$. Let $y$ be the [measured data](/D/data) and let $t_\mathrm{obs} = T(y)$ be the observed test statistic computed from $y$. Moreover, assume that $F_T(t)$ is the [cumulative distribution function](/D/cdf) (CDF) of the distribution of $T(Y)$ under $H_0$.

Then, the p-value is the probability of obtaining a test statistic more extreme than or as extreme as $t_\mathrm{obs}$, given that the null hypothesis $H_0$ is true:

* $p = F_T(t_\mathrm{obs})$, if $H_1$ is a left-sided [one-tailed hypothesis](/D/hyp-tail);
* $p = 1 - F_T(t_\mathrm{obs})$, if $H_1$ is a right-sided [one-tailed hypothesis](/D/hyp-tail);
* $p = 2 \cdot \min \left( \left[ F_T(t_\mathrm{obs}), \, 1 - F_T(t_\mathrm{obs}) \right] \right)$, if $H_1$ is a [two-tailed hypothesis](/D/hyp-tail).

**Theorem:** Under the [null hypothesis](/D/h0), the [p-value](/D/pval) in a [statistical test](/D/test) follows a [continuous uniform distribution](/D/cuni):

$$ p \sim \mathcal{U}(0,1) \;
$$
**Proof:** Without loss of generality, consider a right-sided test.

$$\begin{split}
P &= 1-F_T(T) \\
p &= 1- F_T(t_\mathrm{obs})
\end{split}
$$

where $t_\mathrm{obs}$ is the [observed test statistic](/D/tstat) and $F_T(t)$ is the [cumulative distribution function](/D/cdf) of the [test statistic](/D/tstat) under the [null hypothesis](/D/h0).

Then, we can obtain the [cumulative distribution function](/D/cdf) of the [p-value](/D/pval) as

$$ \begin{split}
F_P(p) &= \mathrm{Pr}(P \leq p) \\
&= \mathrm{Pr}(1 - F_T(T) \leq p) \\
&= \mathrm{Pr}(1-p\leq F_T(T)) \\
&= \mathrm{Pr}(F_T^{-1}(1-p)\leq T) \\
&= 1 - \mathrm{Pr}(T \leq F_T^{-1}(1-p))  \\
&= 1 - F_T(F_T^{-1}(1-p))\\
&= p
\end{split}
$$

So $P$ has a cdf equal to $p$, and thus pdf is equal to 1, which is a uniform distribution.