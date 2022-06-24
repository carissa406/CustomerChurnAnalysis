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

The results show that the only variable not related to Exited was HasCrCard because it's p-value was higher than our alpha = 0.05. We can also see that the mosiac plot for hcct(HasCrCard) is also completely white indicating that there is no relationship between Exited and HasCrCard. HasCrCard variable was then removed.

For comparing the numeric variables with Exited, boxplots and t-tests were used. 

![Box Plots](https://github.com/carissa406/CustomerChurnAnalysis/blob/main/Boxplots.png)

From the t-tests we found that CreditScore, Age, Balance, NumOfProducts, and ActiveMember are all related to Exited. Tenure and EstimatedSalary had higher p-values than our alpha 0.05, therefore, they are not related and we will remove them in the next step.

# Data Analysis and Experimental Results

The data was first trained using logistic regression in the "glm" package in R. We split the data into 80% training and 20% test data. 
Here are the results of the inital model:
The following is a cross table of the model's results.
          actual.label
pred.label Exit Stay
      Exit   87   68
      Stay  316 1529
      
* total_error = 0.192
* false positive rate = .44
* false negative rate = .17

Then, we downsampled the data using the "dplyr" package "sample_n" function. I retrained the model with the new downsampled data to get the following results: 
          actual.label
pred.label Exit Stay
      Exit  270  469
      Stay  133 1128
      
* total error: .2955
* false positives: 0.62
* false negatives: 0.11

In this case, we want to reduce the amount of false negatives meaning that we incorrectly predict that the customer will stay with the bank since that will have the greater impact on the company. The second model is better for this because the false negative rate is lower. However, the total error of this model is greater than the previous.

Second, we will use a c5.0 decision tree model to predict Exited to see if it produces a better or worse result that the logistic regression model.


