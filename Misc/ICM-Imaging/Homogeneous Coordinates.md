Linearity is not maintained when translation is in the form of
$$\begin{aligned}
    \phi_A(x, y) & =
\begin{bmatrix}
        a_{11} & a_{12}\\
        a_{21} & a_{22}
\end{bmatrix}   
\begin{bmatrix}
        x\\
        y
\end{bmatrix}
+
    \begin{bmatrix}
        b_x \\b_y
    \end{bmatrix}
\end{aligned}$$
In order to maintain linearity with translations, we introduce a dummy dimension. In $\mathbb{R}^2$, we have $3\times 3$ matrices in the form
$$\begin{aligned}
    \phi_A(x, y) & =
    \begin{bmatrix}
        (\phi_A)_x(x, y) \\
        (\phi_A)_y(x, y) \\
        1
    \end{bmatrix}
\end{aligned}$$
with
$$\begin{aligned}
    A & =
    \begin{bmatrix}
        a_{11} & a_{12} & b_x \\
        a_{21} & a_{22} & b_y \\
        0      & 0      & 1
    \end{bmatrix}
\end{aligned}$$
It can be verified that this $3\times 3$ matrices form a group.