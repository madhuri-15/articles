### Article Link
[Performance Metrics for Regression Algorithms](https://medium.com/@madhuri15/performance-metrics-for-regression-algorithms-1c889e68fde5)

### Code
```Python
# Import libraries
import pandas as pd
import numpy as np

# Datasets
from sklearn.datasets import load_diabetes
# To split the data
from sklearn.model_selection import train_test_split
# for trainig model
from sklearn.linear_model import LinearRegression

# load data
X, y = load_diabetes(return_X_y=True, as_frame=True)

# split the data into 70% of training data and 30% of testing data.
X_train, X_test, y_train, y_test = train_test_split(X, y, 
                                                    train_size=0.7, 
                                                    random_state=42)

# Training the algorithm Linear Regression
LR_estimator = LinearRegression()
# train the data
LR_estimator.fit(X_train, y_train)
# predicts the output
y_preds = LR_estimator.predict(X_test)
```

#### Types of Regression Metrics
- Mean Absolute Error (MAE)

```python
# Import `mean_absolute_error` method from metric class of sklearn library.
from sklearn.metrics import mean_absolute_error

# Mean Absolute Error
mae = mean_absolute_error(y_test, y_preds)
print("Mean Absolute Error: %.3f" % mae)
#output: Mean Absolute Error: 41.919
```
- Mean Squared Error (MSE)

```python
# Import `mean_square_error` method from metric class of sklearn library.
from sklearn.metrics import mean_squared_error

# Mean Squared Error
mse = mean_squared_error(y_test, y_preds)
print("Mean Squared Error: %.3f" % mse)
# output: Mean Squared Error: 2821.751
```

- Root Mean Squared Error (RMSE)
```python
# for RMSE we will use 'mean_squared_error'.
from sklearn.metrics import mean_squared_error

# first compute MSE
mse = mean_squared_error(y_test, y_preds)

# To calculate RMSE, take sqaure root of MSE
rmse = np.sqrt(mse)
print("Root Mean Squared Error: %.3f" %rmse)
# output: Root Mean Squared Error: 53.120
```
- R2 score
```python
from sklearn.metrics import r2_score

# r2 score
r_squared = r2_score(y_test, y_preds)
print("r-squared score: %0.3f" %(r_squared))
# output: r-squared score: 0.477
```

- Adjusted R2 score

```python
# Calculate adjusted R2_score using r2_score function.
from sklearn.metrics import r2_score

# r2 score
r_squared = r2_score(y_test, y_preds)

# n = Number of observation, k = Number of features.
n, k = X.shape 

Adj_Rsquared = 1 - ((1-r_squared)*(n-1)/(n-k-1))
print("Adjusted r-squared score: %0.3f" %(Adj_Rsquared))
# output: Adjusted r-squared score: 0.465
```
