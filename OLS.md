<h1 align="center">Ordinary Least Sqaure Fit</h1>


The main idea is to optimize the mean square error between the prediction and the original models:

We aim to minimize the following objective function:

$$
\text{Minimize} \quad J(\beta_0, \beta_1, \dots, \beta_n) = \sum_{i = 1}^{n} \left( y^{[i]} - \left( \beta_0 + \sum_{j = 1}^{p} \beta_j x_j^{[i]} \right) \right)^2
$$

However, it is a bit messy to work on this expression. We use the matrix form representation instead.

Define:
- $\mathbf{X}$ as the design matrix, including a column of ones for the intercept:

$$
\mathbf{X} = \begin{bmatrix}
1 & x_1^{[1]} & x_2^{[1]} & \cdots & x_p^{[1]} \\
1 & x_1^{[2]} & x_2^{[2]} & \cdots & x_p^{[2]} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & x_1^{[n]} & x_2^{[n]} & \cdots & x_p^{[n]}
\end{bmatrix}
$$
  
- $\mathbf{y}$ as the vector of observed values:
  
$$
\mathbf{y} = \begin{bmatrix}
y^{[1]} \\
y^{[2]} \\
\vdots \\
y^{[n]}
\end{bmatrix}
$$
  
- $\boldsymbol{\beta}$ as the vector of parameters (coefficients):

$$
\boldsymbol{\beta} = \begin{bmatrix}
\beta_0 \\
\beta_1 \\
\vdots \\
\beta_p
\end{bmatrix}
$$

The model can be written as:

$$
\mathbf{y} = \mathbf{X} \boldsymbol{\beta} + \epsilon
$$

Then the objective function, sum of squared errors can be expressed as:

$$
J(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})
$$

To minimize $J(\boldsymbol{\beta})$, we have different methods for doing so. Here we list the most frequently used methods:
- Closed-form Solution
- Gradient Descent

## Closed-form Solution
To minimize $J(\boldsymbol{\beta})$, take the derivative with respect to $\boldsymbol{\beta}$ and set it to zero:

$$
\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) = 0
$$

This simplifies to:

$$
\mathbf{X}^\top \mathbf{y} = \mathbf{X}^\top \mathbf{X} \boldsymbol{\beta}
$$

⚠️ If the $\mathbf{X}^\top \mathbf{X}$ is invertible, the solution for $\boldsymbol{\beta}$ is:

$$
\boldsymbol{\beta} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y}
$$

The coefficients $\boldsymbol{\beta}$ obtained from this equation minimize the sum of squared errors, providing the best fit line for the data in the least squares sense.

⚠️ If the $X^TX$ is non-invertible, then the OLS may not have a unique solution. Then you should consider using the pseudo-inverse, gradient descent or regularization methods like LASSO or Ridge Regression.

## Gradient Descent Update Rule

To minimize $J(\boldsymbol{\beta})$, we use the gradient descent algorithm. The gradient of the cost function $J(\boldsymbol{\beta})$ with respect to $\boldsymbol{\beta}$ is:

$$
\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})
$$

Initialize the $\boldsymbol{\beta}^{(0)}$ with any real number.
Using gradient descent, the update rule for $\boldsymbol{\beta}$ is:

$$
\boldsymbol{\beta}^{(n+1)} = \boldsymbol{\beta}^{(n)} - \alpha \left(-2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}^{(n)})\right)
$$

Simplify this expression:

$$
\boldsymbol{\beta}^{(n+1)} = \boldsymbol{\beta}^{(n)} + 2 \alpha \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}^{(n)})
$$

Here, $\alpha$ is the learning rate.

