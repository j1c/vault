Bonferroni correction is a method of controlling for [[family-wise error rate]].

Recall that $\alpha$ is the probability that you reject the null $H_0$ when the null is true. We can set the new $\alpha_B=\frac{\alpha}{M}$ where $M$ denotes the number of hypothesis tests. Let $H_k$ denote the hypothesis where $k\in[n]$ and $P_k$ denote the associated p-value for the hypothesis $H_k$. Let $M_0$ denote the number of true hypothesis. To show that $\alpha_B$ controls the FWER to $\alpha$, 

> [!proof]
> $$\begin{align}
> \PP\parens{\bigcup_{k=1}^{M_0}\parens{P_k \leq \alpha_B}}&= \sum_{k=1}^{M_0} \PP\parens{P_k \leq \frac{\alpha}{M}} \tag{Union bound}\\
> &= M_0\frac{\alpha}{M}\\
> &\leq \alpha
> \end{align}$$

The inequality is given since the fraction $\frac{M_0}{M}\leq 1$ since $M_0\leq M$. 