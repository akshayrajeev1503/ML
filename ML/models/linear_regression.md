# ML
Machine learning concepts

## Linear regression

> At its core, Linear Regression is a method to model the relationship between a dependent variable ($y$) and one or more independent variables ($X$).
>
> For a single variable, the model is:
> $$y = mx + c$$
>
> For multiple variables, we use the vectorized form:
> $$y = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_nx_n$$

### Why do we differentiate?
> To find the "best" line, we need to minimize the Loss Function (usually Mean Squared Error). The loss represents the distance between our predictions ($\hat{y}$) and the actual values ($y$).The Intuition:The "Valley": If you plot the Loss Function, it looks like a bowl. The bottom of the bowl represents the minimum error (the best model).The Gradient: Differentiation gives us the slope (gradient) of the bowl at any given point.The Direction: * If the slope is positive, we are on the right side of the valley; we need to decrease our weights.If the slope is negative, we are on the left side; we need to increase our weights.By taking the derivative of the Loss Function with respect to our weights ($\frac{\partial L}{\partial \theta}$), we obtain a mathematical compass that tells us exactly which direction to move to reach the bottom.

### The Power of the Dot Product
> Without Dot Product: You would have to write a loop for every single feature ($x_1, x_2, \dots$) and every single data point. This is extremely slow in Python.With Dot Product: You treat your entire dataset as a matrix $X$. The operation $X \cdot \theta$ calculates the predictions for every row in the dataset simultaneously using optimized C-code under the hood of NumPy.The goal is to find the values of $\theta$ (the weights/parameters) that result in a line (or hyperplane) that passes as close as possible to all data points.

### Vectorized code in Python
```python
import numpy as np
def train_linear_regression_vectorized(X, y, lr=0.01, iterations=1000):
    # 1. Add a column of ones to handle the intercept 'c'
    # This turns [x1, x2] into [1, x1, x2]
    n_samples, n_features = X.shape
    X_b = np.c_[np.ones(n_samples), X]
    
    # 2. Initialize weights to zeros
    # theta[0] is the intercept, theta[1:] are the slopes
    theta = np.zeros(n_features + 1)
    
    for i in range(iterations):
        # 3. Predict all y values at once using Dot Product
        # y_pred = X_b * theta
        y_pred = np.dot(X_b, theta)
        
        # 4. Calculate error (residuals)
        error = y_pred - y
        
        # 5. Calculate Gradients using Dot Product
        # This single line calculates the gradient for EVERY feature at once
        gradients = (2/n_samples) * np.dot(X_b.T, error)
        
        # 6. Update all weights
        theta = theta - lr * gradients
        
    return theta # Returns [intercept, slope1, slope2, ...]
```
