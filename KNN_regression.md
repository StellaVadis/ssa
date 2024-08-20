The main idea of the KNN algorithm is seen as follows:

$$
\begin{align}
d^{[i]} &= \left(x - x^{[i]}\right)^2, \quad i = 1,2,\cdots, n \\
d &= \left[d^{[1]}, d^{[2]}, \cdots, d^{[m]}\right]^T \\
\delta &= \text{min}\_k(d) \\
M(x) &= \frac{\sum_{i=1}^{m} \mathbb{I}(d^{[i]} \leq \delta) \cdot y^{[i]}}{\sum_{i=1}^{m} \mathbb{I}(d^{[i]} \leq \delta)}
\end{align}
$$

where:
- $d$ is the distance between $x$ and $x^{[i]}$
- $\delta$ is the distance threshold 
- $\mathbb{I}(\cdot)$ is the indicator function, which is 1 if the condition inside is true, and 0 otherwise
- $y^{[i]}$ are the response values corresponding to the $i$-th nearest neighbors

We want to design such a model that can compute the predicted features with the available features in dataset and make a prediction based on the voting system. 

However, the $d$ and $K$ are hyperparameters which should be specified by the users. By specifying an appropriate $d$ and $K$, the users may get an implicit model expression. In the real application, we may use the cross-validation technique to find appropriate hyperparameters which optimizes the performance of models, which will not be discussed here.

# 🔍 Example 1

📊 Population Dataset: Invisible

📊 Available Dataset
|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    2    |
| [3] |     9     |     6     |    3    |
| [4] |     4     |     7     |    4    |
| [5] |     8     |     1     |    1    |
| [6] |     7     |     2     |    0    |

🔑 Model Construction

To train a KNN model based on the available dataset, we should consider splitting the dataset randomly into a training set with 4 samples and a test set with 2 samples. For simplicity, let us assume that the $[1],[2],[3],[4]$ are in the training set, while $[4],[5]$ are in the test set.

Then we should select the hyperparameters $K = 2$ and uses Eucleadin Distance $\||x - x'\||_2$. Then the implicit model is constructed as follows:

$$
\begin{align}
d^{[i]} &= \left(x_1 - x_1^{[i]}\right)^2 +  \left(x_2 - x_2^{[i]}\right)^2, \quad i = 1,2,3, 4 \\
d &= \left[d^{[1]}, d^{[2]}, d^{[3]}, d^{[4]}\right]^T \\
\delta &= \text{rank}\_2(d) \\
M(x) &= \frac{\sum\limits_{i=1}^{4} \mathbb{I}\left(d^{[i]} \leq \delta\right) \cdot y^{[i]}}{\sum\limits_{i=1}^{4} \mathbb{I}\left(d^{[i]} \leq \delta\right)}
\end{align}
$$

🔮 Model Inference
Consider making prediction for the $[5]$: 

|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    2    |
| [3] |     9     |     6     |    3    |
| [4] |     4     |     7     |    4    |
| [5] |     8     |     1     |    1    |
| [6] |     7     |     2     |    0    |

$$
\begin{align}
& d\left(x^{[5]},x^{[1]}\right) = \left(8-2\right)^2 + \left(1-3\right)^2 = 40 \\
& d\left(x^{[5]},x^{[2]}\right) = \left(8-5\right)^2 + \left(1-4\right)^2 = 18 \\
& d\left(x^{[5]},x^{[3]}\right) = \left(8-9\right)^2 + \left(1-6\right)^2 = 26 \\
& d\left(x^{[5]},x^{[4]}\right) = \left(8-4\right)^2 + \left(1-7\right)^2 = 52 \\
\end{align}
$$

Then, we can compute that the threshold for [5]: 

$$
\begin{align}
\delta^{[5]} = \text{min}_2 \left( \left[40,18,26,52 \right]^T \right) = 26 
\end{align}
$$

Therefore, the prediction value of [5] is:

$$
\begin{align}
M(x^{[5]}) = \frac{0 \times 1 + 1 \times 2 + 1 \times 3 + 0 \times 4}{0 + 1 + 1 + 0} = 2.5
\end{align}
$$
