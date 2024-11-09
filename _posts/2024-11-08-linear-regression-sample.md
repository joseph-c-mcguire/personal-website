---
title: "Technical Writing Sample: Linear Regression"
author: Joseph McGuire
date: 2024-11-08
header_image: /assets/images/bishop-peak.png
---

## Introduction
Linear regression models the relationship between a dependent variable and one or more independent variables. This technique plays a critical role in many fields, including finance, biology, engineering, and social sciences. You can use linear regression to predict outcomes and uncover relationships. For instance, you might apply linear regression to forecast sales based on advertising expenditures.

## Mathematical Formulation
The purpose of linear regression is to find the line that best fits the data. This line minimizes the sum of the squared differences between the observed values and the predicted values.

### Simple Linear Regression
In simple linear regression, you model the relationship between a dependent variable $y$ and a single independent variable $x$. You express the model as:

$$ y = \beta_0 + \beta_1 x + \epsilon $$

where:
- $y$ represents the dependent variable,
- $x$ represents the independent variable,
- $\beta_0$ is the y-intercept (the value of $y$ when $x = 0$),
- $\beta_1$ is the slope (the change in $y$ per unit change in $x$),
- $\epsilon$ is the error term (the difference between the observed and predicted values).

### Multiple Linear Regression
For multiple linear regression, you extend the model to include more than one independent variable $x_1, x_2, ..., x_p$. The model becomes:

$$
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_p x_p + \epsilon
$$

## Estimating Parameters Using Least Squares
You estimate the parameters $\beta_0$, $\beta_1$ using the least squares method. This method minimizes the sum of squared residuals, where a residual is the difference between the observed and predicted values.

To estimate the parameters $\beta_0$ and $\beta_1$ in simple linear regression, we minimize the sum of squared errors:

$$
S(\beta_0, \beta_1) = \sum_{i=1}^n (y_i - (\beta_0 + \beta_1 x_i))^2
$$

### Numerical Example: Simple Linear Regression
Let’s calculate the parameters using a small dataset. Assume we have the following data points:

| $x_i$ | $y_i$ |
|-------|-------|
| 1     | 2     |
| 2     | 3     |
| 3     | 5     |
| 4     | 7     |
| 5     | 8     |

We will estimate the parameters $\beta_0$ and $\beta_1$ using the least squares method.

#### Step 1: Calculate the Slope ($\beta_1$)
The formula for the slope $\beta_1$ in simple linear regression is:

```math
\beta_1 = \frac{n \sum{x_i y_i} - \sum{x_i} \sum{y_i}}{n \sum{x_i^2} - (\sum{x_i})^2}
```

For our data:

```math
\sum{x_i} = 1 + 2 + 3 + 4 + 5 = 15, \quad \sum{y_i} = 2 + 3 + 5 + 7 + 8 = 25,
\sum{x_i y_i} = 1 \times 2 + 2 \times 3 + 3 \times 5 + 4 \times 7 + 5 \times 8 = 91,
\sum{x_i^2} = 1^2 + 2^2 + 3^2 + 4^2 + 5^2 = 55.
```

Substituting into the formula for `\beta_1`:

```math
\beta_1 = \frac{5 \times 91 - 15 \times 25}{5 \times 55 - 15^2} = \frac{80}{50} = 1.6
```

#### Step 2: Calculate the Intercept (`\beta_0`)
The formula for the intercept `\beta_0` is:

```math
\beta_0 = \frac{\sum{y_i} - \beta_1 \sum{x_i}}{n}
```

Substituting the known values:

```math
\beta_0 = \frac{25 - 1.6 \times 15}{5} = 0.2
```

Thus, the estimated regression equation is:

```math
y = 0.2 + 1.6x
```

## Code Example: Fitting a Linear Regression Model with Python
To apply linear regression in practice, we can use Python and the scikit-learn library. Below is an example of how to fit a linear regression model to the data we used in the previous example.

```python
import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Data points
x = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)  # Independent variable
y = np.array([2, 3, 5, 7, 8])  # Dependent variable

# Create the linear regression model
model = LinearRegression()

# Fit the model
model.fit(x, y)

# Get the parameters
beta_0 = model.intercept_
beta_1 = model.coef_[0]

# Print the regression equation
print(f"The estimated regression equation is: y = {beta_0:.2f} + {beta_1:.2f}x")

# Plot the data points and the fitted line
plt.scatter(x, y, color='blue', label='Data points')
plt.plot(x, model.predict(x), color='red', label='Fitted line')
plt.xlabel('x')
plt.ylabel('y')
plt.title('Linear Regression Fit')
plt.legend()
plt.show()
```

This code will output the regression equation and plot the data points along with the fitted regression line.

## Assumptions of Linear Regression
Linear regression depends on several key assumptions:
- **Linearity**: The relationship between the dependent and independent variables is linear.
- **Independence**: The observations are independent of each other.
- **Homoscedasticity**: The variance of the residuals remains constant across all levels of the independent variables.
- **Normality**: The residuals follow a normal distribution.

### Violation of Assumptions

#### Multicollinearity (Violation of Independence)  
Multicollinearity occurs when two or more independent variables are highly correlated with each other.

#### Heteroscedasticity (Violation of Homoscedasticity)  
Heteroscedasticity occurs when the variance of the residuals changes at different levels of the independent variable(s).

#### Non-Normality of Residuals (Violation of Normality)  
When the residuals are not normally distributed, particularly in small samples, it can lead to invalid hypothesis testing and incorrect confidence intervals.

## Evaluating the Model
You can evaluate the fit of a linear regression model using metrics such as:
- **R-squared**: A measure of how well the model explains the variability in the dependent variable. Higher values indicate better fits.
- **Adjusted R-squared**: A more accurate measure of fit when multiple predictors are used.
- **Mean Squared Error (MSE)**: A measure of the average squared difference between observed and predicted values.

## Real-World Applications of Linear Regression
Linear regression is widely used in various fields. Below are a few examples:
- **Economics**: Predicting GDP growth based on historical economic data, such as inflation rates and unemployment levels.
- **Healthcare**: Predicting patient outcomes (e.g., recovery time, survival rates) based on factors such as age, treatment type, and medical history.
- **Marketing**: Estimating sales based on advertising expenditures or customer demographics.
- **Environmental Science**: Modeling the relationship between environmental factors, such as pollution levels, and public health outcomes.

## Advanced Forms of Regression
While linear regression is useful, it has some limitations, particularly in cases with multicollinearity or when there is a large number of predictors. To address these limitations, more advanced forms of regression can be applied:

### Ridge Regression
Ridge regression is an extension of linear regression that includes a regularization term to prevent overfitting. It adds a penalty to the size of the coefficients, which discourages large values. The ridge regression objective function is:

```math
\hat{\beta}_{ridge} = \underset{\beta_0, \beta_1, \ldots, \beta_p}{\text{argmin}} \left( \sum_{i=1}^n (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^p \beta_j^2 \right)
```

where `λ` is the regularization parameter. Ridge regression is particularly useful when there is multicollinearity in the data.

### Lasso Regression
Lasso regression (Least Absolute Shrinkage and Selection Operator) also adds a penalty to the coefficients, but it uses the L1 norm (absolute value) instead of the L2 norm used in ridge regression. This leads to some coefficients being exactly zero, effectively performing feature selection. The objective function for lasso regression is:

```math
\hat{\beta}_{lasso} = \underset

{\beta_0, \beta_1, \ldots, \beta_p}{\text{argmin}} \left( \sum_{i=1}^n (y_i - \hat{y}_i)^2 + \lambda \sum_{j=1}^p |\beta_j| \right)
```

Lasso regression is particularly useful when you have many predictors and need to perform automatic feature selection.

## Conclusion
Linear regression is a powerful and versatile tool for modeling relationships between variables and making predictions. However, it is important to check the underlying assumptions and evaluate the model's performance using appropriate metrics. In cases where linear regression is not suitable, advanced regression techniques like ridge or lasso regression may be more appropriate.

By understanding the foundations of linear regression, practitioners can effectively apply it to a wide variety of real-world problems, from forecasting to scientific analysis.

## References
1. James, Gareth. "An introduction to statistical learning." (2013).
2. Montgomery, Douglas C., Elizabeth A. Peck, and G. Geoffrey Vining. Introduction to linear regression analysis. John Wiley & Sons, 2021.
