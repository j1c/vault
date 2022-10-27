Benjamini-Hochberg correction is a method of controlling for [[false discovery rate]].

Let $H_1, \ldots, H_n$ be the hypothesis to test, and $n$ is the total number of hypothesis, and $p_1, \ldots, p_n$ be the associated p-values. Assume that the p-values are sorted from smallest to largest.

The Benjamini-Hochberg correction is as follows:
1. For a given $\alpha$, find the largest $k$ such that $p_k\leq \frac{k}{n}\alpha$
2. Reject the hypothesis for all $H_i$ for $i=1, \ldots, k$. 

This is equivalent to saying  find the _largest_ p-value larger than the criterion. Compare to Holm's method (_smallest_ p-value larger than the criterion).


> [!proof]

