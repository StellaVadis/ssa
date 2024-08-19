The main idea of the KNN algorithm is seen as follows:

$$
\begin{align}
d^{[i]} &= \left(x - x^{[i]}\right)^2, \quad i = 1,2,\cdots, n \\
d &= \left[d^{[1]}, d^{[2]}, \cdots, d^{[m]}\right]^T \\
\delta &= \text{rank}\_k(d) \\
M(x) &= \frac{\sum_{i=1}^{m} \mathbb{I}(d^{[i]} \leq \delta) \cdot y^{[i]}}{\sum_{i=1}^{m} \mathbb{I}(d^{[i]} \leq \delta)}
\end{align}
$$

where:
$$
\begin{aligned}
&\bullet \quad d \text{ is the distance between } x \text{ and } X \\
&\bullet \quad \delta \text{ is the distance threshold based on the 3rd ranked distance} \\
&\bullet \quad \mathbb{I}(\cdot) \text{ is the indicator function, which is 1 if the condition inside is true, and 0 otherwise} \\
&\bullet \quad Y^{[i]} \text{ are the response values corresponding to the } i\text{-th nearest neighbors}
\end{aligned}
$$

# Training Algorithm
This model does not contain parameters to be trained.
