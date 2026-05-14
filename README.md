# Linear-Regression
Linear Regression is one of the most well-known algorithms in machine learning and statistics. Here, you will be given a brief overview of how it works and how you can use it in your machine learning problems. Linear Regression was developed under the field of statistics to study the relationship between input and output numerical variables but has been borrowed by machine learning to make predictions based on a linear regression equation.

The mathematical representation of linear regression is a linear equation that combines a specific set of input data (X) to predict the output value (y) for that set of input values. The linear equation assigns a factor to each set of input values, which are called the coefficients represented by the Greek letter Beta (β). The equation mentioned below represents a linear regression model with two sets of input values,  𝑥1 and  𝑥2 . Ahead, y represents the output of the model, whereas  β0 ,  β1 and  β2 are the coefficients of the linear equation.

𝑦=β0+β1∗𝑋1+β2∗𝑋2

Imports & Data
Scikit-Learn library is used to perform the linear regression and has some of very common datasets to play with.


import pandas as pd
# Import matplotlib as an alias plt and set the style
import matplotlib.pyplot as plt
%matplotlib inline
plt.style.use('seaborn-v0_8-darkgrid')
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score, explained_variance_score

# The data is stored in the directory 'data'
path = '../data/'

# Read the csv file using read_csv method of pandas
df = pd.read_csv(path + 'SPY.csv', index_col=0)

# Convert index to datetime format
df.index = pd.to_datetime(df.index)

# Print the first five rows 
df.head()
