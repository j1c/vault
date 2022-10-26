---
author:
- Jaewon Chung
title: Introduction to Computational Medicine Notes
cards-deck: Introduction to Computational Medicine Notes
---
# Systems Model of Computational Anatomy
This class will revolve around studying the following equations:

$$\begin{align}
I& = \phi_t \cdot I_{temp} \tag{Observer Equation} \\
\dot{\phi}_t & = v_t \circ \phi_t \tag{Dynamics Equation}
\end{align}$$
$\phi_t$ is the _flow_ that aligns the template image, $I_{temp}$ to the target image, $I$. For example, many MRI images can be aligned using flow to a template, or atlas, image. The rate of change, $\dot\phi_t$, is given by the velocity $v_t$ at its position $\phi_t$. This class will focus on studying $\phi_t$ and $v_t$.

## Theory of Transformations
$$\begin{aligned}
I & = \phi_t \cdot I_{temp}
\end{aligned}$$
The flow, $\phi_t$, is indexed by time $t$. $\phi_t$ is a matrix and $I_{temp}$ is a vector. Transformations are [[mapping functions]]. In $\mathbb{R}^2$, let the transformation coordinates be $(x, y)\in\mathbb{R}^2$ and the transformation function $\phi: (x, y) \rightarrow \phi(x, y) = \left\lparen \phi_x(x, y), \phi_y(x, y)\right\rparen\in\mathbb{R}^2$.

> [!example]
> **Example 3**. Transformations by matrices on vectors
> $$\begin{aligned}
> \phi_A & = \underbrace{
> \begin{bmatrix}
> a_{11} & a_{12} \\
> a_{21} & a_{22}
> \end{bmatrix}
> }_A
> \begin{bmatrix}
> x \\
> y
> \end{bmatrix}
> \end{aligned}$$
> Other examples include
> - Translations:
> $$\begin{aligned}
>\phi(x, y) & = \begin{bmatrix} x\\ y \end{bmatrix}
>+
>\begin{bmatrix} b_x\\b_y\end{bmatrix}\end{aligned}$$
> - Scaling:
> $$\begin{aligned}
>\phi(x, y) & = \begin{bmatrix}
>s_x & 0 \\ 0 & s_y
> \end{bmatrix}\begin{bmatrix} x\\ y \end{bmatrix}
> \end{aligned}$$
> - Rotation:
> $$\begin{aligned}
>\phi(x, y) & = \begin{bmatrix}
>\cos\theta & -\sin\theta \\ \sin\theta & \cos\theta
>\end{bmatrix}\begin{bmatrix} x\\ y \end{bmatrix}
> \end{aligned}$$ 

## Spline Models of Images
This model is build from vector fields and landmark constraints.
- Measured landmarks: $\phi(x_i), i\in[n]$ where $i$ indexes different points, or landmarks. Note that $x_i$ and $\phi(x_i)$ are givens and we often want to find the transformation that best approximates the movement of $x_i$ to $\phi(x_i)$.
- Unknown vector field: $\phi(x) = x + v(x)$ where $x\in\mathbb{R}^3$.

Landmarks provide boundary conditions.
- Vector field :
$$\begin{aligned}
(v_x(x, y), v_y(x, y)), (x, y)\in\mathbb{R}^2 \\
\underbrace{
\begin{bmatrix}
\phi_x(x, y) \\
\phi_y(x,y)
\end{bmatrix}
}_{\phi(x,y)} =
\underbrace{
\begin{bmatrix}
x \\y
\end{bmatrix}
}_{\vec x}
\underbrace{
\begin{bmatrix}
v_x(x, y) \\ v_y(x, y)
\end{bmatrix}
}_{v(x,y)}

\end{aligned}$$
- Boundary conditions: landmarks in $\mathbb{R}^2$
$$\begin{aligned}
\begin{bmatrix}
\phi_x(x_i, y_i) \\
\phi_y(x_i,y_i)
\end{bmatrix} & =
\begin{bmatrix}
x_i \\y_i
\end{bmatrix}
+
\begin{bmatrix}
v_x(x_i, y_i) \\ v_y(x_i, y_i)
\end{bmatrix}

\end{aligned}$$
where $i$ indexes the landmarks.
## Estimation of Translations based on Landmarks
We aim to estimate the translation $\phi(x) = x+b$ where $b=\begin{bmatrix}b_x \\b_y\end{bmatrix}\in\mathbb{R}^2$ with boundary conditions $\phi(x_i), i\in[n]$ where $i$ indexes the boundary points. Thus, the solution is
$$\begin{aligned}
\min_{b_x, b_y} E(b) & = \sum_i\left\lVert \phi(x_i) - (x_i + b) \right\rVert_2^2\\
 & =\sum_i\left\lVert (\phi(x_i) - x_i) + b \right\rVert_2^2\\

 & = \sum_i\left\lVert (\phi(x_i) - x_i) \right\rVert_2^2 + \sum_i\left\lVert b \right\rVert_2^2 - 2\sum_i\left\lVert \phi(x_i) - x_i \right\rVert\cdot b
\end{aligned}$$
The $(\phi(x_i) - x_i)$ is constant since we are minimizing over $b$. Thus, the problem simplifies to
$$\begin{aligned}

\arg\min_b \frac{1}{2}nb\cdot b - \sum_i(\phi(x_i) - x_i)\cdot b

\end{aligned}$$
We solve the above by taking the gradient respect to $b$. Below is the [[Computational Medicine Standard Form]].
$$\begin{aligned}
\hat E (b)& = \frac{1}{2}nb\cdot b -\sum_i(\phi(x_i) - x_i)\cdot b \\
\nabla \hat E (b) & = nb - \sum_i(\phi(x_i) - x_i) = 0\\
b & = \frac{1}{n} \sum_i(\phi(x_i) - x_i)
\end{aligned}$$

## Estimation of Scale-Rotation based on Landmarks
We aim to estimate the transformation $\phi(x) = Ax, A\in GL(2)$ with boundary conditions $\phi(x_i), i\in[n]$. The solution is given by

$$\begin{aligned}

\arg\min_A E(A) & = \sum_i \left\lVert \phi(x_i)-Ax_i \right\rVert_2^2\\

& = \sum_i \left\lVert \phi(x_i) \right\rVert_2^2 + \sum_i\left\lVert Ax_i \right\rVert^2_2 - 2\sum_i \phi(x_i)\cdot Ax_i

\end{aligned}$$

We transform the transformation and landmark points as follows:
$$\begin{aligned}

Ax_i & =

\begin{bmatrix}

a_{11} & a_{12}\\

a_{21} & a_{22}

\end{bmatrix}



\begin{bmatrix}

x_i\\

y_i

\end{bmatrix}

\\

 & =

\underbrace{

\begin{bmatrix}

x_i & y_i & 0& 0\\

0& 0& x_i & y_i

\end{bmatrix}

\begin{bmatrix}

a_{11} \\ a_{12} \\ a_{21} \\ a_{22}

\end{bmatrix}

}_{\bar{X_i}\bar a}

\end{aligned}$$
Note that the matrix multiplication still results in the same vector $\begin{bmatrix}a_{11}x_i + a_{12}y_i \\ a_{21}x_i + a_{22}y_i\end{bmatrix}$.
The solution can be formed in the [[Computational Medicine Standard Form]]:

$$\begin{aligned}
\arg\min_A E(\bar a) & = \sum_i \left\lVert \phi(x_i) \right\rVert_2^2 + \sum_i\left\lVert Ax_i \right\rVert^2_2 - 2\sum_i \phi(x_i)\cdot Ax_i\\
 & = \frac{1}{2}\sum_i \bar X_i^T\bar X_i\bar a \cdot \bar a - \sum_i \bar X_i^T \phi(x_i)\cdot \bar a \\
\nabla E(\bar a) & =
\sum_i \bar X_i^T\bar X_i\bar a - \sum_i \bar X_i^T \phi(x_i) = 0\\
\hat{\bar a} & =
\left\lparen \sum_i \bar X_i^T\bar X_i\right\rparen^{-1}
\left\lparen \sum_i \bar X_i^T \phi(x_i)\right\rparen
\end{aligned}$$

## Estimation of Scale-Rotation + Translation Based on Landmarks

Recall from [Section-Homogenous Coordinates](#homogeneous-coordinates) that homogeneous coordinates can be added to account for translations. We aim to estimate $phi(x^h) = A^hx^h$ where $A^h =\begin{bmatrix}a_{11} & a_{12} & b_x \\a_{21} & a_{22} & b_y \\0& 0& 1\end{bmatrix}$ and $x^h = \begin{bmatrix}x \\y\\1\end{bmatrix}$
with boundary conditions $\phi(x_i), i\in[n]$. We have the following solution:
$$\begin{aligned}
\arg\min_{A^h} E(A^h) & = \sum_i \left\lVert \phi(x_i^h) - A^hx_i^h \right\rVert_2^2\\
& = \sum_i \left\lVert \phi(x_i^h) \right\rVert_2^2 + \sum_i \left\lVert A^hx_i^h \right\rVert_2^2 - 2\sum_i \phi(x_i^h)\cdot A^hx_i^h
\end{aligned}$$
We transform the transformation and landmark points as follows:
$$\begin{aligned}
Ax_i & =
\begin{bmatrix}
a_{11} & a_{12} & b_x \\
a_{21} & a_{22} & b_y \\
0& 0& 1
\end{bmatrix}
\begin{bmatrix}
x \\y\\1
\end{bmatrix} \\
& =
\underbrace{
\begin{bmatrix}
x_i & y_i & 0& 0& 0 & 0 \\
0& 0& x_i & y_i & 1 & 0 \\
0& 0& 0& 0& 0 & 1
\end{bmatrix}
\begin{bmatrix}
a_{11} \\ a_{12} \\b_x \\ a_{21} \\ a_{22} \\b_y \\ 1
\end{bmatrix}
}_{\bar{X_i}\bar a}
\end{aligned}$$
Similarly, we have the solution in the computational medicine standard form
$$\begin{aligned}
\arg\min_A E(\bar a) & = \sum_i \left\lVert \phi(x_i) \right\rVert_2^2 + \sum_i\left\lVert Ax_i \right\rVert^2_2 - 2\sum_i \phi(x_i)\cdot Ax_i\\
& = \frac{1}{2}\sum_i \bar X_i^T\bar X_i\bar a \cdot \bar a - \sum_i \bar X_i^T \phi(x_i)\cdot \bar a\\
\nabla E(\bar a) & =
\sum_i \bar X_i^T\bar X_i\bar a - \sum_i \bar X_i^T \phi(x_i) = 0\\
\hat{\bar a}& =
\left\lparen \sum_i \bar X_i^T\bar X_i\right\rparen^{-1}
\left\lparen \sum_i \bar X_i^T \phi(x_i)\right\rparen
\end{aligned}$$