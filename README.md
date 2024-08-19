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

$$ 
\begin{align}
\text{minimize} \quad  \text{MAE} = \frac{1}{n} \sum_{i=1}^{n} \left| M\left(x_1^{[i]}, x_2^{[i]}, \cdots, x_d^{[i]} \right) - y^{[i]} \right|
\end{align}
$$


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

\indent 💡 The $$R^2$$ metric is a useful measure of the goodness of fit for your model. The numerator represents the Mean Squared Error (MSE) of your model's predictions, while the denominator represents the MSE when all predictions are simply the mean value of $y$ (the simplest possible model). Essentially, $$R^2$$ indicates how much better your model performs compared to this baseline model that only predicts the mean.

- Adjusted R-squared (\(R^2_{adj}\)):

$$
\begin{align}
\text{maximize} \quad R^2_{adj} = 1 - \left(1 - R^2\right) \times \frac{n - 1}{n - d - 1}
\end{align}
$$
