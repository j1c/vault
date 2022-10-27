Bonferroni correction is a method of controlling for [[family-wise error rate]].

Recall that $\alpha$ is the probability that you reject the null $H_0$ when the null is true. We can set the new $\alpha_B=\frac{\alpha}{n}$ where $n$ denotes the number of hypothesis tests. Let $H_k$ denote the hypothesis where $k\in[n]$ and $P_k$ denote the associated p-value for the hypothesis $H_k$. Let $n_0$ denote the number of true hypothesis. To show that $\alpha_B$ controls the FWER to $\alpha$, 

> [!proof]
> $$\begin{align}
> \PP\parens{\bigcup_{k=1}^{n_0}\parens{P_k \leq \alpha_B}}&= \sum_{k=1}^{n_0} \PP\parens{P_k \leq \frac{\alpha}{n}} \tag{Union bound}\\
> &= n_0\frac{\alpha}{n}\\
> &\leq \alpha
> \end{align}$$

The inequality is given since the fraction $\frac{n_0}{n}\leq 1$ since $n_0\leq n$. 