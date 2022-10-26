# Green's Function
For any linear, time invariant operator $A$, then the system is linear time-invariant system (LTI).
^1665528221434


> [!defn] 
> **Definition 1** (Linear Time-Invariant Systems). *For a system with input $x(t)$ and output $y(t)$, denoted $x(t) \rightarrow y(t)$, LTI system has two properties:* #card
> 1.  Linearity:
>     $$\begin{aligned}
>                       x(t)\rightarrow y(t) & \implies cx(t) \rightarrow cy(t) \forall c\in\mathbb{R}
>     \end{aligned}$$
>     and
>     $$\begin{aligned}
>                       \begin{rcases}
>                           x_1(t) \rightarrow  y_1(t) \\
>                           x_2(t)\rightarrow y_2(t)
>                       \end{rcases}\implies
>                       x_1(t) + x_2(t) \rightarrow y_1(t) + y_2(t)
>     \end{aligned}$$
> 2.  Time invariance:
>     $$\begin{aligned}
>                       x(t) \rightarrow y(t) \implies x(t-t_0)\rightarrow y(t-t_0) \forall t_0\in\mathbb{R}
>     \end{aligned}$$
> 
^1665529304375

One useful property of LTI is that knowing the output from a particular input allows us to compute the output from any other input. This particular input is the delta function ($\delta(t)$).

> [!defn]
> title: (Unit-step function). #card
> The unit-step function $u_s(x)$ is defined as
> $$\begin{aligned}
>         u_s(t) = \begin{cases}
>             1 & x \geq 0  \\
>             0 & otherwise
>         \end{cases}
> \end{aligned}$$
> 
^1665529211224

> [!defn] 
> **Definition 3** (Dirac Delta Function). Also known as the unit impulse.  #card
> In discrete case, it is defined as
> $$\begin{aligned}
>         \delta(t) =\begin{cases}
>             1 & t=0       \\
>             0 & otherwise
>         \end{cases}
> \end{aligned}$$
> 
> *In continuous case, it is defined with two properties*
> 1.  *$\delta(t) = 0, \forall t\neq 0$*
> 2.  *$\int_{-\infty}^\infty \delta(t) dt = 1$*
> 3.  *$\int_a^b \delta(t)f(t)dt = f(0)$ if $a <0$ and $b>0$*
> 4.  *$\frac{d}{dx}u_s(x) = \delta(x)$*
> 
> *One way to think of continuous delta function is as 0 everywhere except $t=0$ where it is infinite.*
^1665529211227


> [!exercise]
> **Exercise 2**. Show that
> $$\begin{aligned}
>         \int_{-a}^b \delta(\tau)d\tau = 1
> \end{aligned}$$

> [!proof]
> In order for the integral to evaluate to 1, the integral interval must contain 0. Hence, we have that
> $$\begin{aligned}
>             \int_{-\infty}^{-a} \delta(\tau)d\tau & = 0 \\
>             \int_b^\infty \delta(\tau)d\tau       & = 0
\end{aligned}$$
Hence, the integral in the interval $(-a, b)$ is
> $$\begin{aligned}
> \int_{-a}^b \delta(\tau)d\tau &= 1        
> \end{aligned}$$ 
> 

 While the proof is simply a use of the definition, a more concrete way to show is to assume that the delta function is a probability distribution, which must integrate to 1 over its support. The strict definition is not relevant for this class.

> [!exercise]
**Exercise 3**. *Show that
$$x(t)\ast \delta(t) = \int_{-\infty}^\infty x(\tau)\delta(t-\tau)d\tau = x(t)$$*

> [!proof]

```ad-defn
**Definition 4** (Green's function). #card 
Given a linear, time invariant operator $A$, any solution $k(x)$ in the form of
$$Ak(x)  =\delta(x)$$ is a Green's function.
```

In this class, how Green's functions are found is not relevant.

> [!exercise]
**Exercise 4**. *Show that below are Green's functions*
> 1.  *$A = \frac{d}{dx}+1 \rightarrow k(x) = e^{-x}u_s(x)$*
> 2.  *$A = -\frac{d}{dx}+1 \rightarrow k(x) = e^{x}u_s(x)$

> [!proof]
We want to show that $Ak(x) = \delta(x)$. Recall that $u_s$
> 1.  $$\begin{aligned}
>                           Ak(x) & =\left\lparen \frac{d}{dx}+ 1\right\rparen\left\lparen e^{-x}u_s(x)\right\rparen \\
>                                 & = \frac{d}{dx}e^{-x}u_s(x) + e^{-x}u_s(x)        \\
>     \end{aligned}$$
>     Recall the product rule of derivatives:
>     $$\frac{d(uv)}{dx} = u\frac{dv}{dx} + v\frac{du}{dx}$$
>     Using the product rule, we have
>     $$\begin{aligned}
>                           \frac{d}{dx}e^{-x}u_s(x) + e^{-x}u_s(x) & = e^{-x} \delta(x) - e^{-x} u_s(x) + e^{-x}u_s(x) \\
>                                                                   & = e^{-x}\delta(x)                                 \\
>                                                                   & =\delta(x)
>     \end{aligned}$$
>     The last line is given by the fact that $\delta(x)=1$ only when $x=0$.
> 
> 2.  $$\begin{aligned}
>                           Ak(x) & =\left\lparen -\frac{d}{dx}+ 1\right\rparen\left\lparen e^{x}u_s(-xx)\right\rparen   \\
>                                 & = -\frac{d}{dx}e^{x}u_s(-x) + e^{x}u_s(-x)           \\
>                                 & = -\left\lparen e^x\delta(-x) + e^xu_s(-x)\right\rparen + e^xu_s(-x) \\
>                                 & = -e^x\delta(-x)                                     \\
>                                 & = \delta(x)
>     \end{aligned}$$
> 
>  ◻

Once the Green's function $k(x)$ is found for the differential operator $A$, then the solutions for the general input, $p(x)$, can be obtained with convolution
$$\begin{aligned}
    \delta(x)\rightarrow k(x) \implies p(x) \rightarrow p(x)\ast k(x)
\end{aligned}$$
