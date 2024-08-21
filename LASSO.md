<h1 align="center">LASSO Regression</h1>

LASSO (Least Absolute Shrinkage and Selection Operator) Regression is a type of linear regression that includes an L1 regularization term. This regularization term can lead to sparse models by setting some coefficients to zero, effectively performing feature selection.

### Objective Function

The objective function for LASSO Regression is:

$$
\text{Minimize} \quad J(\boldsymbol{\beta}) = \sum_{i = 1}^{n} \left( y^{[i]} - \left( \beta_0 + \sum_{j = 1}^{p} \beta_j x_j^{[i]} \right) \right)^2 + \lambda \sum_{j = 1}^{p} |\beta_j|
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

Then the objective function with L1 regularization can be expressed as:

$$
J(\boldsymbol{\beta}) = (\mathbf{y} - \mathbf{X} \boldsymbol{\beta})^\top (\mathbf{y} - \mathbf{X} \boldsymbol{\beta}) + \lambda \boldsymbol{1}^\top |\boldsymbol{\beta}|
$$

where $|\boldsymbol{\beta}|$ denotes the element-wise absolute value of $\boldsymbol{\beta}$.

### Coordinate Descent

Since the LASSO problem involves an L1 penalty, there is no closed-form solution. Instead, coordinate descent is commonly used. The coordinate descent algorithm updates each coefficient $\beta_j$ while keeping the others fixed. The update for $\beta_j$ is given by:

$$
\beta_j^{\text{new}} = \frac{1}{n} \left( \text{soft} \left( \frac{\mathbf{r}_j + \mathbf{X}_{\text{j}} \beta_j^{\text{old}}}{n}, \frac{\lambda}{2} \right) \right)
$$

where $\text{soft}(a, b)$ is the soft-thresholding operator defined as:

$$
\text{soft}(a, b) = \text{sgn}(a) \max(|a| - b, 0)
$$

In this update:
- $\mathbf{r}_j$ is the residual for feature $j$.
- $\mathbf{X}_{\text{j}}$ is the column of $\mathbf{X}$ corresponding to feature $j$.
- $\text{sgn}(a)$ is the sign function, which returns +1 for $a > 0$, -1 for $a < 0$, and 0 for $a = 0$.

### Steps in Coordinate Descent

1. **Initialize** $\boldsymbol{\beta}$ with zeros or another starting point.
2. **Iteratively update** each $\beta_j$ using the coordinate descent update rule.
3. **Repeat** until convergence, which is typically determined when the changes in $\boldsymbol{\beta}$ are below a specified tolerance level.

### Summary

LASSO Regression adds an L1 regularization term to the least squares objective, which encourages sparsity in the model coefficients. Due to the non-differentiability of the L1 norm, coordinate descent is used to find the optimal coefficients. This method updates each coefficient iteratively, making it possible to handle the sparsity-inducing penalty effectively.

