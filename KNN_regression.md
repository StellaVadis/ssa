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
- $d$ is the distance between $x$ and $x^{[i]}$
- $\delta$ is the distance threshold 
- $\mathbb{I}(\cdot)$ is the indicator function, which is 1 if the condition inside is true, and 0 otherwise
- $y^{[i]}$ are the response values corresponding to the $i$-th nearest neighbors

We want to design such a model that can compute the predicted features with the available features in dataset and make a prediction based on the voting system. 

However, the $d$ and $k$ are hyperparameters which should be specified by the users. By specifying an appropriate $d$ and $k$, the users may get an implicit model expression. In the real application, we may use the cross-validation technique to find appropriate hyperparameters which optimizes the performance of models, which will not be discussed here.

# 🔍 Example 1
|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    0    |
| [3] |     9     |     6     |    1    |
| [4] |     4     |     7     |    1    |
| [5] |     8     |     1     |    0    |
| [6] |     7     |     2     |    1    |
| [7] |     6     |     4     |    0    |
| [8] |     4     |     2     |    1    |
| [9] |     5     |     7     |    0    |
| [10] |    6     |     5     |    1    |
| [11] |    7     |     3     |    1    |
| [12] |    3     |     8     |    0    |
| [13] |    2     |     5     |    1    |
| [14] |    8     |     4     |    0    |
| [15] |    6     |     7     |    1    |
| [16] |    1     |     3     |    0    |
| [17] |    9     |     5     |    1    |
| [18] |    3     |     2     |    0    |
| [19] |    7     |     6     |    1    |
| [20] |    4     |     1     |    0    |
