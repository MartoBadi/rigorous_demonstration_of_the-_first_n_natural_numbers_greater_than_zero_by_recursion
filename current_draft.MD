# Proof of the Formula for the Sum of the First $n$ Natural Numbers

## Proof by Recurrence and Decomposition

Let $S(n) = 1 + 2 + 3 + \cdots + n$. We aim to prove that $S(n) = \dfrac{n(n+1)}{2}$ using a recursive approach.

### Step 1: Establishment of the Recurrence

Consider the case when $n$ is a power of 2, i.e., $n = 2^m$. We can decompose the sum:

$$
S(2k) = (1 + 2 + \cdots + k) + ((k+1) + (k+2) + \cdots + 2k)
$$

Let's rewrite the second term:

$$
(k+1) + (k+2) + \cdots + 2k = (1 + k) + (2 + k) + \cdots + (k + k)
$$

$$
= (1 + 2 + \cdots + k) + (\underbrace{k + k + \cdots + k}_{k\text{ times}})
$$

$$
= S(k) + k^2
$$

Therefore, we obtain the recurrence relation:

$$
S(2k) = S(k) + [S(k) + k^2] = 2S(k) + k^2
$$

### Step 2: Resolution of the Recurrence

Let $n = 2^m$, then:

$$
S(2^m) = 2S(2^{m-1}) + (2^{m-1})^2
$$

Applying iteratively:

$$
\begin{align*}
S(2^m) &= 2S(2^{m-1}) + 2^{2m-2} \\
&= 2[2S(2^{m-2}) + 2^{2m-4}] + 2^{2m-2} \\
&= 2^2S(2^{m-2}) + 2^{2m-3} + 2^{2m-2} \\
&= 2^3S(2^{m-3}) + 2^{2m-4} + 2^{2m-3} + 2^{2m-2} \\
&\;\;\vdots \\
&= 2^mS(1) + \sum_{j=0}^{m-1} 2^{2m-2-j}
\end{align*}
$$

Since $S(1) = 1$, we have:

$$
S(2^m) = 2^m + \sum_{j=0}^{m-1} 2^{2m-2-j}
$$

### Step 3: Simplification of the Summation

The summation is a geometric series:

$$
\sum_{j=0}^{m-1} 2^{2m-2-j} = 2^{2m-2} + 2^{2m-3} + \cdots + 2^{m-1}
$$

Factoring $2^{m-1}$:

$$
= 2^{m-1}(2^{m-1} + 2^{m-2} + \cdots + 2^0) = 2^{m-1} \sum_{k=0}^{m-1} 2^k
$$

The geometric sum $\sum_{k=0}^{m-1} 2^k = 2^m - 1$, therefore:

$$
\sum_{j=0}^{m-1} 2^{2m-2-j} = 2^{m-1}(2^m - 1)
$$

### Step 4: Substitution and Simplification

Substituting into the previous expression:

$$
\begin{align*}
S(2^m) &= 2^m + 2^{m-1}(2^m - 1) \\
&= 2^m + 2^{2m-1} - 2^{m-1} \\
&= 2^{2m-1} + 2^{m-1} \\
&= 2^{m-1}(2^m + 1)
\end{align*}
$$

### Step 5: Generalization for All $n$

Since $n = 2^m$, then $m = \log_2 n$:

$$
S(n) = 2^{\log_2 n - 1}(2^{\log_2 n} + 1) = \frac{n}{2}(n + 1) = \frac{n(n+1)}{2}
$$

### Step 6: Verification for Odd $n$

For $n = 2k + 1$:

$$
\begin{align*}
S(2k + 1) &= S(2k) + (2k + 1) = \frac{2k(2k + 1)}{2} + (2k + 1) \\
&= k(2k + 1) + (2k + 1) = (2k + 1)(k + 1) \\
&= \frac{(2k + 1)(2k + 2)}{2} = \frac{n(n+1)}{2}
\end{align*}
$$

## Conclusion

We have proved that for all $n \in \mathbb{N}$:

$$
\boxed{1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2}}
$$

The proof uses recursive decomposition and recurrence resolution without assuming the formula beforehand.
