> [!defn] 
> Frobenius norm is the $l_2$ norm denoted $\norm{\cdot}_F$ is a [[Matrix norm]]. For all $A, B\in\Mn$,
> $$\begin{align}
> \norm{AB}_F^2 &= \sum_{i,j}\abs{\sum_k a_{ik}b_{kj}}^2\\
> &\leq \sum_{i,j,k}|a_{ik}|^2|b_{kj}|^2\tag{Cauchy-Schwarz}\\
> &\leq \sum_{i,j,k,l}|a_{ik}|^2|b_{lj}|^2\\
> &= \sum_{i,k} |a_{ik}|^2\sum_{l,j}|b_{lj}|^2\\
> &= \norm{A}_F^2\norm{B}_F^2
> \end{align}$$

