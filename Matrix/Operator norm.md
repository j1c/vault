> [!defn]
> Suppose $A\in\Mmn$ where $A$ is a function from $A:\CC^n_{l_p} \rightarrow \CC^m_{l_q}$ . The operator norm is defined as
> $$\begin{align}
> \norm{A}_{p, q} &= \max_{x\neq 0} \frac{\norm{Ax}_q}{\norm{x}_p}
> \end{align}
> $$



> [!defn] 
> For $A\in\Mmn, \norm{A}_{2, 2}^2=\sigma_1(A)$ or the largest singular value of $A$. 

> [!proof]
> $$\begin{align}
> \norm{A}_{2, 2}^2 &= \max_{x\neq 0} \frac{\norm{Ax}_2^2}{\norm{x}_2^2} \\
> &= \max_{x\neq 0}\frac{x^*A^*Ax}{x^*x} \\
> &= \lambda_1(A^*A) \\
> &= \sigma^2_1(A)
> \end{align}$$
> Second to last line is given by Rayleigh-Ritz

