Group, $(G, \circ)$, has laws of composition, identity and inverse.
1.  Composition: for all $g, h\in G, ~g\circ h\in G$
2.  Identity: for all $g \in G, g \circ I = g$
3.  Inverse: for all $g\in G, g^{-1}\circ g = I \in G$
^1665525988632

```ad-example 
* Examples of groups include integers, $(0, \infty)$.
``` 

```ad-example
**Example 2** (Generalized linear group). This group consists of $N\times N$ matrices with non-zero determinants (i.e. invertible). For example,
$$\begin{aligned}
        G & = \left\lbrace 2\times 2 ~matrices : A =
            \begin{bmatrix}
                a_{11} & a_{12} \\
                a_{21} & a_{22}
            \end{bmatrix}, \det A  \neq 0
         \right\rbrace
\end{aligned}$$
* Rotation group consists of matrices with $\det = 1$ (i.e. orthogonal matrices).
$$\begin{align}
        G & = \left\lbrace 2\times 2 ~matrices : A =
            \begin{bmatrix}
                \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta
            \end{bmatrix}, \det A  =1
         \right\rbrace
\end{align}$$
* Scaling group consists of diagonal matrices.
$$\begin{aligned}
        G & = \left\lbrace 2\times 2 ~matrices : A =
            \begin{bmatrix}
                s_1 & 0 \\ 0 & s_2
            \end{bmatrix}, \det A  \neq 0
         \right\rbrace
\end{aligned}$$
* Any transformation $\phi_A(x, y) = \begin{bmatrix}a_{11} & a_{12} \\a_{21} & a_{22}        \end{bmatrix} \begin{bmatrix}            x & y        \end{bmatrix}\in \mathbb{R}^2, \det A \neq 0$ can be decomposed as composition of a rotation, scaling and rotation.
$$\begin{aligned}
        \phi_A(x, y) & = \begin{bmatrix}
            a_{11} & a_{12} \\
            a_{21} & a_{22}
        \end{bmatrix} \\
                     & =
        \begin{bmatrix}
            \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta
        \end{bmatrix}
        \begin{bmatrix}
            \rho_1 & 0 \\ 0 & \rho_2
        \end{bmatrix}
        \begin{bmatrix}
            \cos\gamma & -\sin\gamma \\ \sin\gamma & \cos\gamma
        \end{bmatrix}
\end{aligned}$$
Which is essentially an eigendecomposition.
```

```ad-exercise
**Exercise 1**. *Show that if $A$ and $B$ are orthogonal, then the product is also orthogonal.*

```ad-proof
Matrix $A\in M_n(\mathbb{R})$ is orthogonal if $AA^T = A^TA = I$.
$$\begin{aligned}
            (AB)(AB)^T & = ABB^TA^T \\
                       & = AIA^T    \\
                       & = I
\end{aligned}$$
Hence, $AB$ is orthogonal. ◻
```

*One way to interpret the result is that orthogonal matrices are rotation matrices (or change of basis). Product of rotation matrices is similar to rotating a vector twice, which is still a rotation.*