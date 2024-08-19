# Model Construction

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

# Model Inference
