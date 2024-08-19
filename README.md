# Regression

## Task Description
A regression task is a type of problem in machine learning and statistics where the goal is to predict a continuous output value based on input data. 

## Dataset
|     |  $x_1$   |  $x_2$   |  $x_3$   |  ...  |  $x_d$   | $y$  |
|-----|:------------:|:------------:|:------------:|:-----:|:------------:|:--------:|
| [1] |  $x_1^{[1]}$ |  $x_2^{[1]}$ |  $x_3^{[1]}$ |  ...  |  $x_d^{[1]}$ | $y^{[1]}$ |
| [2] |  $x_1^{[2]}$ |  $x_2^{[2]}$ |  $x_3^{[2]}$ |  ...  |  $x_d^{[2]}$ | $y^{[2]}$ |
| [3] |  $x_1^{[3]}$ |  $x_2^{[3]}$ |  $x_3^{[3]}$ |  ...  |  $x_d^{[3]}$ | $y^{[3]}$ |
| ... |      ...      |      ...      |      ...      |  ...  |      ...      |    ...   |
| [n] |  $x_1^{[n]}$ |  $x_2^{[n]}$ |  $x_3^{[n]}$ |  ...  |  $x_d^{[n]}$ | $y^{[n]}$ |

## Evaluation Metrics

Find a model $M(\cdot)$ such that:

- Mean Absolute Error (MAE):


<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MathJax Example with Background Color</title>
    <style>
        .math-container {
            background-color: #f0f0f0; /* 浅灰色背景 */
            padding: 10px; /* 内边距 */
            border-radius: 5px; /* 边角圆润 */
            overflow: auto; /* 确保公式内容不会溢出 */
            margin: 20px 0; /* 外边距 */
        }
        .math-container pre {
            margin: 0; /* 去掉pre标签的默认外边距 */
        }
    </style>
</head>
<body>

<div class="math-container">
    $$ 
    \begin{align}
    \text{minimize} \quad  \text{MAE} = \frac{1}{n} \sum_{i=1}^{n} \left| M\left(x_1^{[i]}, x_2^{[i]}, \cdots, x_d^{[i]} \right) - y^{[i]} \right|
    \end{align}
    $$
</div>

<!-- MathJax Script -->
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

</body>
</html>


- Mean Squared Error (MSE):

$$
\begin{align}
\text{minimize} \quad \text{MSE} = \frac{1}{n} \sum_{i=1}^{n} \left( M\left(x_1^{[i]}, x_2^{[i]}, \cdots, x_d^{[i]} \right) - y^{[i]} \right)^2
\end{align}
$$

- Root Mean Squared Error (RMSE):

$$
\begin{align}
\text{minimize} \quad \text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} \left( M\left(x_1^{[i]}, x_2^{[i]}, \cdots, x_d^{[i]} \right) - y^{[i]} \right)^2}
\end{align}
$$

- R-squared $$\left(R^2\right)$$:

$$
\begin{align}
& \bar{y} = \frac{1}{n} \sum_{i=1}^{n} y^{[i]} \\
\text{maximize} \quad & R^2 = 1 - \frac{\sum_{i=1}^{n} \left( M\left(x_1^{[i]}, x_2^{[i]}, \cdots, x_d^{[i]} \right) - y^{[i]} \right)^2}{\sum_{i=1}^{n} \left( y^{[i]} - \bar{y} \right)^2}
\end{align}
$$

- Adjusted R-squared (\(R^2_{adj}\)):

$$
\begin{align}
\text{maximize} \quad R^2_{adj} = 1 - \left(1 - R^2\right) \times \frac{n - 1}{n - d - 1}
\end{align}
$$
