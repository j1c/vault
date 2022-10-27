> [!defn] 
> A  norm $\norm{\cdot}$ on $\Mn(\mathbb K)$ over $\mathbb K$ is a matrix norm if in addition to [[Vector norm|norm]] properties, it satisfies for all $A, B\in \Mn(\mathbb K)$
> $$\begin{align}\norm{AB}\leq \norm{A}\norm{B}\end{align}$$

> [!example]
> Consider vector norms (that is norms from [[Normed linear space]]). That is consider the matrix as just a single long vector. Then $l_1$ on $\Mn(\mathbb K)$ is 
> $$\begin{align}\norm{A}_1 &= \sum_{i,j}|a_{ij}| \end{align}$$
> 
> We can show submultiplicity.
> $$\begin{align}
> \norm{AB}_1 &= \sum_{i,j}\abs{\sum_k a_{ik}b_{kj}}\\
> &\leq \sum_{i,j,k}\abs{a_{ik}}\abs{b_{kj}}\tag{Cauchy-Schwarz}\\
> &\leq \sum_{i,j,k,l}|a_{ik}||b_{lj}|\\
> &= \sum_{i,k} |a_{ik}|\sum_{l,j}|b_{lj}| = \norm{A}_1\norm{B}_1
> \end{align}$$

> [!example]
> $l_\infty$ is not a matrix norm.

