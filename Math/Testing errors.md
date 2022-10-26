# Types of errors

We have a null hypothesis $H_0$, and after observing some data, we want to accept or reject $H_0$.
1. Type 1 (false positive) - $H_0$ is true, but we reject it.
2. Type 2 (false negative) - $H_0$ is not true, but we accept it. 

Classical statistical decision theory has two goals:
1. Guarantee that the probability of a Type 1 error is below a pre-specified level $\alpha$ (usually 5%) 
2. Maximize the power, i.e. minimize the probability of Type 2 error, subject to the previous constraint.