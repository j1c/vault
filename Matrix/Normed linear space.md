> [!defn]
> Normed linear space (NLS) is a tuple of vector space $V$ over field $\mathbb{K}$ and a [[vector norm]] $\norm{\cdot}$.

> [!defn]
> If $(V,\langle \cdot,\cdot\rangle)$ is an [[Inner product space]] over $\mathbb K$, then define $\norm{\cdot}$ (norm induced by [[inner product]]) as for all $x\in V$, $\norm{\cdot} = \sqrt{\langle \cdot,\cdot\rangle}$. The pair $(V, \norm{\cdot})$ is a normed linear space.


> [!proof]
> We show that the norm induced by the inner product satisfies the triangle inequality property of vector norms.
> For $x, y\in V$
> $$
> \begin{align}
> \norm{x+y}^2 &= \iprod{x+y}{x+y}\\
> &= \iprod{x}{x}+ \iprod{x}{y} + \iprod{y}{x} + \iprod{y}{y} \\
> &= \norm{x}^2+\norm{y}^2 + 2\iprod{x}{y}\\
> &\leq \norm{x}^2+\norm{y}^2 + 2\norm{x}\norm{y}\\
> &= (\norm{x}+\norm{y})^2
> \end{align}
> $$
