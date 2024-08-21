<h1 align="center">Linear Regression</h1>

----

$$ 
M(x_1,x_2,x_3) = 1937.964582 -5.157235 x_1 + 496.6025 x_2 + 1116.807677 x_3 
$$ 

----

To get the model, we just use the simplest way of linear regression. Firstly, we randomly separate the dataset into train and test dataset with a ratio of 7:3. 

- Train Indices: 12,  48,  86,  29,  94,   6,  67,  66,  36,  17,  50,  35,   8,
             96,  28,  20,  82,  26,  63,  14,  25,   4,  18,  39,   9,  79,
              7,  65,  37,  90,  57, 100,  55,  44,  51,  68,  47,  69,  62,
             98,  80,  42,  59,  49,  99,  58,  76,  33,  95,  60,  64,  85,
             38,  30,   2,  53,  22,   3,  24,  88,  92,  75,  87,  83,  21,
             61,  72,  15,  93,  52
- Test Indices: 84, 54, 71, 46, 45, 40, 23, 81, 11,  1, 19, 31, 74, 34, 91,  5, 77,
            78, 13, 32, 56, 89, 27, 43, 70, 16, 41, 97, 10, 73

Then we fit the linear regression model by computing:

$\beta = (X^TX)^{-1}X^Ty$, and round the result into 6 decimal points, which yields that:

$$
M(x_1,x_2,x_3) = 1937.964582 -5.157235 x_1 + 496.6025 x_2 + 1116.807677 x_3
$$

We also compute the evaluation metrics:\
Training Set MAD: 72.18050734762957\
Training Set MSE: 8340.06694071241\
Training Set RMSE: 91.32396695672178\
Training Set R-squared: 0.979544712974249\
Test Set MAD: 74.77093912630646\
Test Set MSE: 8689.619505183051\
Test Set RMSE: 93.21812862948414\
Test Set R-squared: 0.9833155409384102\
Population MAD: 83.3727744983166\
Population MSE: 10883.980736279285\
Population RMSE: 104.32631852164288\
Population R-squared: 0.9791080689152433

⚠ Population Metrics are invisible to users. We can compute it because this is artificial dataset
