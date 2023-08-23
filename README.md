# SurpriseHousing_AdvancedRegression
Advanced Regression for House Price Prediction

## Problem Statement - Part 1
A US-based housing company named Surprise Housing has decided to enter the Australian market. The company uses data analytics to purchase houses at a price below their actual values and flip them on at a higher price. For the same purpose, the company has collected a data set from the sale of houses in Australia. The data is provided in the CSV file below.

The company is looking at prospective properties to buy to enter the market. You are required to build a regression model using regularisation in order to predict the actual value of the prospective properties and decide whether to invest in them or not.

The company wants to know:

- Which variables are significant in predicting the price of a house, and
- How well those variables describe the price of a house.

Also, determine the optimal value of lambda for ridge and lasso regression.

__Business Goal__

You are required to model the price of houses with the available independent variables. This model will then be used by the management to understand how exactly the prices vary with the variables. They can accordingly manipulate the strategy of the firm and concentrate on areas that will yield high returns. Further, the model will be a good way for management to understand the pricing dynamics of a new market.

## Problem Statement - Part 2

__Question 1__

What is the optimal value of alpha for ridge and lasso regression? What will be the changes in the model if you choose double the value of alpha for both ridge and lasso? What will be the most important predictor variables after the change is implemented?

__Question 2__

You have determined the optimal value of lambda for ridge and lasso regression during the assignment. Now, which one will you choose to apply and why?

__Question 3__

After building the model, you realised that the five most important predictor variables in the lasso model are not available in the incoming data. You will now have to create another model excluding the five most important predictor variables. Which are the five most important predictor variables now?

__Question 4__

How can you make sure that a model is robust and generalisable? What are the implications of the same for the accuracy of the model and why?

## Approach:
1. Data Understanding, Preparation and EDA
 
    - Reading the dataset
    - Separating the numerical and categorical features
    
      A. Analysing numerical data
        - Univariate and Bivariate analysis of the numeric data
        - Analysing numeric features with continous values
        - Analysing numeric features with discrete values
        - Missing value handling of numeric features
          
      B. Analysing categorical data
        - Missing value handling of categorical features
        - Analysing ordered features
        - Encoding For Categorical Variables

2. Model Building and Evaluation
    - Splitting into Train and Test Data
    - Feature Scaling
    - Initial Feature Selection with RFE
    - Ridge Regression
    - Lasso Regression
    - Comparing Model Coefficients
    - Final Model Selection  

## Conslusion

1. First the housing data is read and analyzed dividing the features into numerical and categorical types.

2. SalePrice is the target column here.

3. All the features are then analyzed, missing data handling, outlier detection, data cleaning are done. Trend of SalePrice is observed for change in individual features.

4. New features are extracted, redundant features dropped and categorical features are encoded accordingly.

5. Then the data in split into train and test data and feature scaling is performed.

6. Target variable SalePrice is right skewed. Natural log of the same is Normal distributed, hence for model building, natural log of SalePrice is considered.

7. Creating dummy variables increased the number of features greatly, highly imbalanced columns are dropped.

8. Top 50 features are selected through RFE and adjusted R-square.

9. Ridge and Lasso Regression Model are built with optimum alpha calculated in GridSearchCV method. Optimum alpha = 10.0 for ridge and 0.0001 for lasso model.

10. Model evaluation is done with R2 score and Root Mean Square Error (RSME).

11. Lasso Regression is chosen as final model for having slightly better R-square value on test data.

12. Out of 50 features in the final model, top 10 features in order of descending importance are: ['1stFlrSF', '2ndFlrSF', 'OverallQual', 'OverallCond', 'SaleCondition_Partial', 'LotArea', 'SaleCondition_Normal','BsmtFinSF1', 'MSZoning_RL', 'BsmtQual']

13. Model coefficients are listed in a table along with the corresponding features , for example natural log of SalePrice will change by 0.123923 with unit change in the feature '1stFlrSF' when all the features remain constant.

14. Negative sign in the coefficient signifies negative correlation between the predictor and target variable.

15. Predicted value of SalePrice is tranformed into its original scale by performing antilog.

16. The houses should be bought When the market value of the property is lower than the Predicted Sale Price.
