
Convolution of two signals $x(t)$ and $y(t)$ describes how one signal blends with another as one function is shifted over the other. For discrete signals, it is defined as
$$\begin{aligned}
    y(t) \ast x(t) & = \sum_{\tau=-\infty}^\infty y(\tau)x(t-\tau)
\end{aligned}$$
and for continuous signals as
$$\begin{aligned}
    y(t) \ast x(t) & = \int_{-\infty}^{\infty}y(\tau)x(t-\tau) d\tau
\end{aligned}$$
^1665528154164

```ad-example
**Example 4**. *Show $y(t)\ast x(t) = x(t) \ast y(t)$*
```
