The main idea is to optimize the mean square error between the prediction and the original models:

We aim to minimize the following objective function:

$$
\text{Minimize} \quad J(\beta_0, \beta_1, \dots, \beta_n) = \sum_{i = 1}^{n} \left( y^{[i]} - \left( \beta_0 + \sum_{j = 1}^{p} \beta_j x_j^{[i]} \right) \right)^2
$$

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
