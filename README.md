# Predicting Customer Churn Using Logistic Regression and Decision Trees
This was an assignment completed during my coursework at the University of Illinois. The churn modeling dataset was provided to us by the instructor which contains 10,000 observations of bank customer information. I demonstrate the use of logistic regression and decision trees as well as downsampling techniques to predict customer churn.

[Click to see my code](https://github.com/carissa406/CustomerChurnAnalysis/blob/main/Churn.Rmd)

#Problem Definition and Goals
The purpose of this analysis is to utilize logistic regression and decision tree model to predict customer churn at a bank given their attributes. There are 10,000 observations of 11 variables in the raw data. RowNumber, CustomerId, and Surname variables were removed since they are not relevant to the analysis at hand. Our target variable is Exited.

#Data Exploration and Preprocessing
First, the categorical variables that were associated with our target variable (Exited) will be identified using Mosiac Plots and Chi Squared tests. Variables that were not related to our target variable were removed. 
