# Predicting Customer Churn Using Logistic Regression and Decision Trees
This was an assignment completed during my coursework at the University of Illinois. The churn modeling dataset was provided to us by the instructor which contains 10,000 observations of bank customer information. I demonstrate the use of logistic regression and decision trees as well as downsampling techniques to predict customer churn.

[Click to see my code](https://github.com/carissa406/CustomerChurnAnalysis/blob/main/Churn.Rmd)

# Problem Definition and Goals
The purpose of this analysis is to utilize logistic regression and decision tree model to predict customer churn at a bank given their attributes. There are 10,000 observations of 11 variables in the raw data. RowNumber, CustomerId, and Surname variables were removed since they are not relevant to the analysis at hand.
We are left with the following variables:
- CreditScore
- Geography
- Gender
- Age
- Tenure
- Balance
- NumOfProducts
- HasCrCard
- IsActiveMember
- EstimatedSalary
- Exited (target)

# Data Exploration and Preprocessing
First, the categorical variables that were associated with our target variable (Exited) will be identified using Mosiac Plots and Chi Squared tests. A Mosiac Plot in R is very useful to visualize the data from a contingency table or two-way frequency table. 
- Red block means observed cell
frequency is lower than the expected
cell frequency if the data were random
- Blue block means observed cell
frequency is higher than the expected
cell frequency if the data were random
- White block means there is not much
difference between the observed and
expected frequency if data were
random
Variables that were not related to our target variable were removed. 


![Mosaic Plots](https://github.com/carissa406/CustomerChurnAnalysis/blob/main/mosaicplots.png)

Pearson's Chi-squared test with Yates' continuity correction
data:  hcct
X-squared = 0.47134, df = 1, p-value = 0.4924

The results show that the only variable not related to Exited was HasCrCard because it's p-value was higher than our alpha = 0.05. We can also see that the mosiac plot for hcct(HasCrCard) is also completely white indicating that there is no relationship between Exited and HasCrCard. HasCrCard variable was then removed.

For comparing the numeric variables with Exited, boxplots and t-tests were used. 



