<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>居中的大标题</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .centered-title {
            text-align: center;
            font-size: 3em; /* 设置字体大小，3em 是一个大标题的常用值 */
            margin-top: 20px; /* 可以根据需要调整顶部边距 */
        }
    </style>
</head>
<body>

    <h1 class="centered-title">Regression</h1>

</body>
</html>

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
