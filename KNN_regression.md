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

However, the $d$ and $K$ are hyperparameters which should be specified by the users. By specifying an appropriate $d$ and $K$, the users may get an implicit model expression. In the real application, we may use the cross-validation technique to find appropriate hyperparameters which optimizes the performance of models, which will not be discussed here.

# 🔍 Example 1

Population Dataset (Invisible to Users)
|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    2    |
| [3] |     9     |     6     |    3    |
| [4] |     4     |     7     |    4    |
| [5] |     8     |     1     |    1    |
| [6] |     7     |     2     |    0    |
| [7] |     6     |     4     |    0    |
| [8] |     4     |     2     |    1    |
| [9] |     5     |     7     |    2    |
| [10] |    6     |     5     |    1    |
| [11] |    7     |     3     |    4    |
| [12] |    3     |     8     |    6    |
| [13] |    2     |     5     |    7    |
| [14] |    8     |     4     |    2    |
| [15] |    6     |     7     |    1    |
| [16] |    1     |     3     |    0    |
| [17] |    9     |     5     |    0    |
| [18] |    3     |     2     |    1    |
| [19] |    7     |     6     |    2    |
| [20] |    4     |     1     |    4    |

Available Dataset
|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    2    |
| [3] |     9     |     6     |    3    |
| [4] |     4     |     7     |    4    |
| [5] |     8     |     1     |    1    |
| [6] |     7     |     2     |    0    |

🔑 Solution

To train a KNN model based on the available dataset, we should consider splitting the dataset randomly into a training set with 4 samples and a test set with 2 samples. For simplicity, let us assume that the $[1],[2],[3],[4]$ are in the training set, while $[4],[5]$ are in the test set.

Then we should select the hyperparameters $K = 2$ and uses Eucleadin Distance $\||x - x'\||$.
