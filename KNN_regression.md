The main idea of the linear regression is seen as follows:

$$
\begin{align}
M(x_1,x_2,\cdots,x_d) = b + \sum_{j = 1}^{d} w_j x_j
\end{align}
$$
The main idea is to optimize the mean square error between the prediction and the original models:

We aim to minimize the following objective function:

\[
\text{Minimize} \quad J(\beta_0, \beta_1, \dots, \beta_n) = \sum_{i = 1}^{n} \left( y^{[i]} - \left( \beta_0 + \sum_{j = 1}^{p} \beta_j x_j^{[i]} \right) \right)^2
\]

1. Matrix Form Representation

Let's express the problem in matrix form. Define:
- \( \mathbf{X} \) as the design matrix, including a column of ones for the intercept:
  \[
  \mathbf{X} = \begin{bmatrix}
  1 & x_1^{[1]} & x_2^{[1]} & \cdots & x_p^{[1]} \\
  1 & x_1^{[2]} & x_2^{[2]} & \cdots & x_p^{[2]} \\
  \vdots & \vdots & \vdots & \ddots & \vdots \\
  1 & x_1^{[n]} & x_2^{[n]} & \cdots & x_p^{[n]}
  \end{bmatrix}
  \]
  
- \( \mathbf{y} \) as the vector of observed values:
  \[
  \mathbf{y} = \begin{bmatrix}
  y^{[1]} \\
  y^{[2]} \\
  \vdots \\
  y^{[n]}
  \end{bmatrix}
  \]
  
- \( \boldsymbol{\beta} \) as the vector of parameters (coefficients):
  \[
  \boldsymbol{\beta} = \begin{bmatrix}
  \beta_0 \\
  \beta_1 \\
  \vdots \\
  \beta_p
  \end{bmatrix}
  \]

The model can be written as:
\[
\mathbf{y} = \mathbf{X} \boldsymbol{\beta} + \boldsymbol{\epsilon}
\]
where \( \boldsymbol{\epsilon} \) is the error vector.

2. Objective Function in Matrix Form

The sum of squared errors can be expressed as:
\[
J(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})
\]

3. Differentiation with Respect to \( \boldsymbol{\beta} \)

To minimize \( J(\boldsymbol{\beta}) \), take the derivative with respect to \( \boldsymbol{\beta} \) and set it to zero:
\[
\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) = 0
\]

This simplifies to:
\[
\mathbf{X}^\top \mathbf{y} = \mathbf{X}^\top \mathbf{X} \boldsymbol{\beta}
\]

4. Solution for \( \boldsymbol{\beta} \)

Assuming \( \mathbf{X}^\top \mathbf{X} \) is invertible, the solution for \( \boldsymbol{\beta} \) is:
\[
\boldsymbol{\beta} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y}
\]

5. Final Result

The coefficients \( \boldsymbol{\beta} \) obtained from this equation minimize the sum of squared errors, providing the best fit line for the data in the least squares sense.

# 🔍 Example 1
📊 Available Dataset

<div align="center">

|     |   $x_1$   |   $x_2$   |   $y$   |
|-----|:---------:|:---------:|:-------:|
| [1] |     2     |     3     |    1    |
| [2] |     5     |     4     |    2    |
| [3] |     9     |     6     |    3    |
| [4] |     4     |     7     |    4    |
| [5] |     8     |     1     |    1    |
| [6] |     7     |     2     |    0    |

</div>


🔑 Model Construction

To train a KNN model based on the available dataset, we should consider splitting the dataset randomly into a training set with 4 samples and a test set with 2 samples. For simplicity, let us assume that the $[1],[2],[3],[4]$ are in the training set, while $[4],[5]$ are in the test set.

Then we should select the hyperparameters $K = 2$ and uses Eucleadin Distance $\||x - x'\||_2$. Then the implicit model is constructed as follows:

$$
\begin{align}
d^{[i]} &= \left(x_1 - x_1^{[i]}\right)^2 +  \left(x_2 - x_2^{[i]}\right)^2, \quad i = 1,2,3, 4 \\
d &= \left[d^{[1]}, d^{[2]}, d^{[3]}, d^{[4]}\right]^T \\
\delta &= \text{min}\_2(d) \\
M(x) &= \frac{\sum\limits_{i=1}^{4} \mathbb{I}\left(d^{[i]} \leq \delta\right) \cdot y^{[i]}}{\sum\limits_{i=1}^{4} \mathbb{I}\left(d^{[i]} \leq \delta\right)}
\end{align}
$$

🔮 Model Inference

Consider making prediction for the $[5]$: 

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
M\left(x^{[5]}\right) = \frac{0 \times 1 + 1 \times 2 + 1 \times 3 + 0 \times 4}{0 + 1 + 1 + 0} = 2.5
\end{align}
$$


Consider making prediction for the $[6]$: 

$$
\begin{align}
& d\left(x^{[6]},x^{[1]}\right) = \left(7-2\right)^2 + \left(2-3\right)^2 = 26 \\
& d\left(x^{[6]},x^{[2]}\right) = \left(7-5\right)^2 + \left(2-4\right)^2 = 8 \\
& d\left(x^{[6]},x^{[3]}\right) = \left(7-9\right)^2 + \left(2-6\right)^2 = 20 \\
& d\left(x^{[6]},x^{[4]}\right) = \left(7-4\right)^2 + \left(2-7\right)^2 = 34 \\
\end{align}
$$

Then, we can compute that the threshold for [6]: 

$$
\begin{align}
\delta^{[6]} = \text{min}_2 \left( \left[26,8,20,34 \right]^T \right) = 20 
\end{align}
$$

Therefore, the prediction value of [6] is:

$$
\begin{align}
M\left(x^{[6]}\right) = \frac{0 \times 1 + 1 \times 2 + 1 \times 3 + 0 \times 4}{0 + 1 + 1 + 0} = 2.5
\end{align}
$$

🧮 Model Evaluation

We evaluate the metrics on test dataset:

$$
\begin{align}
\text{MSE} = \frac{(2.5-1)^2+(2.5-0)^2}{2} = 4.25
\end{align}
$$

$$
\begin{align}
& \text{MAE} = \frac{\left|2.5-1\right| + \left|2.5-0\right|}{2} = 2 \\
& \text{MSE} = \frac{(2.5-1)^2+(2.5-0)^2}{2} = 4.25 \\
& \text{RMSE} = \sqrt{4.25} \\
& \bar{y} = \frac{1+2+3+4}{2} = 2.5 \\
& R^2 = 1 - \frac{(2.5-1)^2+(2.5-0)^2}{(2.5-1)^2 + (2.5 - 0)^2} = 0
\end{align}
$$

The $R^2 = 0$ means that the model is no better than just make prediction using mean value, which is therefore considered a bad model.
