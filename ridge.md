<h1 align="center">Ridge Regression</h1>

Ridge Regression is an extension of Ordinary Least Squares (OLS) that includes a regularization term to handle multicollinearity and overfitting. The goal is to minimize the sum of squared errors while also penalizing large coefficients.

### Objective Function

The objective function for Ridge Regression is:

$$
\text{Minimize} \quad J(\boldsymbol{\beta}) = \sum_{i = 1}^{n} \left( y^{[i]} - \left( \beta_0 + \sum_{j = 1}^{p} \beta_j x_j^{[i]} \right) \right)^2 + \lambda \sum_{j = 1}^{p} \beta_j^2
$$

where $\lambda$ is the regularization parameter.

### Matrix Form Representation

Define:
- **$\mathbf{X}$** as the design matrix, including a column of ones for the intercept:

$$
\mathbf{X} = \begin{bmatrix}
1 & x_1^{[1]} & x_2^{[1]} & \cdots & x_p^{[1]} \\
1 & x_1^{[2]} & x_2^{[2]} & \cdots & x_p^{[2]} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & x_1^{[n]} & x_2^{[n]} & \cdots & x_p^{[n]}
\end{bmatrix}
$$
  
- **$\mathbf{y}$** as the vector of observed values:

$$
\mathbf{y} = \begin{bmatrix}
y^{[1]} \\
y^{[2]} \\
\vdots \\
y^{[n]}
\end{bmatrix}
$$
  
- **$\boldsymbol{\beta}$** as the vector of parameters (coefficients):

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

Then the objective function, sum of squared errors with regularization, can be expressed as:

$$
J(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) + \lambda \boldsymbol{\beta}^\top \boldsymbol{\beta}
$$

### Algorithm to Find the Solution
- Closed-form Solution
- Gradient Descent

### Closed-form Solution

To minimize $J(\boldsymbol{\beta})$, take the derivative with respect to $\boldsymbol{\beta}$ and set it to zero:

$$
\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) + 2 \lambda \boldsymbol{\beta} = 0
$$

This simplifies to:

$$
\mathbf{X}^\top \mathbf{y} = \mathbf{X}^\top \mathbf{X} \boldsymbol{\beta} + \lambda \boldsymbol{\beta}
$$

Rearrange to:

$$
(\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I}) \boldsymbol{\beta} = \mathbf{X}^\top \mathbf{y}
$$

⚠️ If $\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I}$ is invertible, the solution for $\boldsymbol{\beta}$ is:

$$
\boldsymbol{\beta} = (\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I})^{-1} \mathbf{X}^\top \mathbf{y}
$$

The coefficients $\boldsymbol{\beta}$ obtained from this equation minimize the regularized sum of squared errors, providing the best fit line with Ridge regularization.

⚠️ The term $\lambda \mathbf{I}$ ensures that the matrix $\mathbf{X}^\top \mathbf{X} + \lambda \mathbf{I}$ is always invertible, which mitigates issues of non-invertibility present in OLS.

### Gradient Descent Update Rule

To minimize $J(\boldsymbol{\beta})$ using gradient descent, the gradient of the cost function $J(\boldsymbol{\beta})$ with respect to $\boldsymbol{\beta}$ is:

$$
\frac{\partial J(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} = -2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) + 2 \lambda \boldsymbol{\beta}
$$

Initialize $\boldsymbol{\beta}^{(0)}$ with any real number. Using gradient descent, the update rule for $\boldsymbol{\beta}$ is:

$$
\boldsymbol{\beta}^{(n+1)} = \boldsymbol{\beta}^{(n)} - \alpha \left(-2 \mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}^{(n)}) + 2 \lambda \boldsymbol{\beta}^{(n)}\right)
$$

Simplify this expression:

$$
\boldsymbol{\beta}^{(n+1)} = \boldsymbol{\beta}^{(n)} + 2 \alpha \left(\mathbf{X}^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}^{(n)}) - \lambda \boldsymbol{\beta}^{(n)}\right)
$$

Here, $\alpha$ is the learning rate.
