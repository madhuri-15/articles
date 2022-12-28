### Article Link
[ML Algorithm: Linear Regression from scratch using gradient descent](https://medium.com/@madhuri15/ml-algorithm-linear-regression-from-scratch-using-gradient-descent-algorithm-6639ae8663c)

### Code
```python
# Linear Regression implementation from scratch using Gradient descent

# importing libraries
import csv
import numpy as np
import matplotlib.pyplot as plt

def linear_models(X, y, learning_rate=0.01, epochs=500):
    
    w = 0
    b = 0
    n = len(X) # Number of observations

    for i in range(epochs):
        y_hat = predict(w, b, X) # Predicting values using w and b
        error = y_hat - y        # computing error

        # partial derivative equation on cost function with respect to w and b
        delta_w = 2/n * (np.sum(error * X))
        delta_b = 2/n * (np.sum(error))

        # update values of w and b
        temp_w = w - learning_rate * delta_w
        temp_b = b - learning_rate * delta_b

        w = temp_w
        b = temp_b 

    return w, b


def predict(w, b, X):
    y_hat = b + w*X
    return y_hat


def mean_squared_error(y_hat, y):
    error = y_hat - y
    return np.sum((error)**2) / len(y)

def plots(X, y, y_hat):

    # scatter plot of data points and best fit regression line.
    plt.scatter(X, y,)
    plt.plot(X, y_hat, label="best-fit line")

    plt.xlabel("Size")
    plt.ylabel("Price")
    plt.title("Scatter plot")

    plt.legend()
    plt.show()


def main():
    '''
    # Regression data.
    column 0: Area of House
    column 1: Price of House 
    '''

    # reading data
    reg_data = []
    with open('data.csv', 'r', newline='\n') as f:
        data = csv.reader(f, delimiter=',')
        for row in data:
            reg_data.append(row)

    X = np.array([float(row[0]) for row in reg_data])
    y = np.array([float(row[1]) for row in reg_data])
    
    w, b = linear_models(X, y, learning_rate=0.03, epochs=1500)
    y_predict = predict(w, b, X)
    mse = mean_squared_error(y_predict, y)

    # plots
    plots(X, y, y_predict)


if __name__ == "__main__":
    main()
```
