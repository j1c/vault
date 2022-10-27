Let $H_1, \ldots, H_n$ be the hypothesis to test, and $n$ is the total number of hypothesis, and $p_1, \ldots, p_n$ be the associated p-values. Assume that the p-values are sorted from smallest to largest.

Procedure:
1. Order the [[p-value]]s from smallest to largest. 
2. Check if $p_1\leq \frac{\alpha}{n}$
	- If yes, reject.
3. Check if $p_2\leq\frac{\alpha}{n-1}$
	- If yes, reject.
4. Repeat until you do not reject. Let the index  denote 
5. Accept all $H_{n+1-m}$

> [!proof]
> Let $I$ be the set of indices of the true hypothesis, and $|I|=m$. Then we have that the FWER is equivalent to
> $$\begin{align}
> \PP\parens{\bigcap_{i\in I} p_i > \frac{\alpha}{m}} &
> = 1 - \PP\parens{\bigcup_{i\in I} p_i \leq \frac{\alpha}{m}}\\
> &\geq 1 - \sum_{i\in I}\PP\parens{p_i \leq \frac{\alpha}{m}} \tag{Union bound}\\
> & \geq 1- m\frac{\alpha}{m} = 1-\alpha
> \end{align}$$
> This means that 
> $$\begin{align}
> 1 - \PP\parens{\bigcup_{i\in I} p_i \leq \frac{\alpha}{m}} &\geq 1-\alpha\\
> -\PP\parens{\bigcup_{i\in I} p_i \leq \frac{\alpha}{m}} &\geq -\alpha\\
> \PP\parens{\bigcup_{i\in I} p_i \leq \frac{\alpha}{m}} &\leq \alpha
> \end{align}$$


Why is Holm-Bonferroni uniformly more powerful than [[Bonferroni correction]]? In Holm-Bonferroni, the p-values are compared to the numbers
$$
\frac{\alpha}{n}, \frac{\alpha}{n-1}, \ldots, \frac{\alpha}{1}$$
whereas classical Bonferroni compares all p-values to $\alpha/n$. This means that the probability of rejecting any set of (false) hypotheses using the classical Bonferroni test is smaller than or equal to the same probability using the sequentially rejective Bonferroni test based on the same test statistics. Thus, Holm-Bonferroni test can replace where Bonferroni test has been used. 