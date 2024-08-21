<h1 align="center">Sales Regression</h1>

----
📊 Dataset
- [Population Dataset](https://github.com/StellaVadis/ssa/edit/main/sales_population.md) 
- [Available Dataset](https://github.com/StellaVadis/ssa/edit/main/sales_available.md)
----

🧩 Variable Description

- $x_1$: Price
- $x_2$: Promotion
- $x_3$: SeasonFactor
- $y$: Sales
----

🚀 Model

$$
\begin{align}
M(x_1,x_2,x_3)
\end{align}
$$

----

📐 Evaluation Metrics

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

----

🎯 Model Performance

<table>
  <thead>
    <tr>
      <th rowspan="2">Model Name</th>
      <th colspan="4">Population Metrics</th>
      <th colspan="4">Reported Metrics</th>
    </tr>
    <tr>
      <th>MAE</th>
      <th>MSE</th>
      <th>RMSE</th>
      <th>$$R^2$$</th>
      <th>MAE</th>
      <th>MSE</th>
      <th>RMSE</th>
      <th>$$R^2$$</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://github.com/StellaVadis/ssa/blob/main/sales_linear.md">Linear Regression</a></td>
      <td>83.3728</td>
      <td>10883.9807</td>
      <td>104.3263</td>
      <td>0.9791</td>
      <td>74.7709</td>
      <td>8689.6195</td>
      <td>93.2181</td>
      <td>0.9833</td>
    </tr>
    <tr>
      <td><a href="https://github.com/StellaVadis/ssa/blob/main/sales_knn.md">Standardized KNN</a></td>
      <td>152.8579</td>
      <td>38045.9113</td>
      <td>195.0536</td>
      <td>0.9270</td>
      <td>172.6786</td>
      <td>47159.1680</td>
      <td>217.1616</td>
      <td>0.9095</td>
    </tr>
    <tr>
      <td>Model 3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Model 4</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

----


