# PA17_3: Classification Project on Predicting Likelihood of Success of Banking Product Marketing Campaign

_Link to corresponding Jupyter notebook:_
https://github.com/pamelakhalaf/PA17_3/blob/main/Code/FINAL_prompt_III_bankingcampaign_PK.ipynb

## Problem Statement 
This project is aimed at developing a predictive algorithm to inform whether a client will subscribe a term deposit as a result of a phone based marketing campaign. The model is based on a bank marketing campaign dataset and multiple supervised predictive algorithms are explored and hyperparameter tuned. 

## EDA 
### Data Understanding 
The dataset used to explore this question comes from the UC Irvine Machine Learning Repository and is based on a collection of results of marketing campaigns from a Portuguese banking institution. The original dataset consists of ~ 41,200 entries, 20 client & social/economic features in addition to the target variable of whether a client accepted the bank term deposit following the marketing call. The dataset includes both numerical and categorical features with some of the categorical features having an "unknown" or "non-existent" value. Only 12 dupicates were found in the dataset. 

### Data Cleaning and Preparation
In preparation for supervised classification algorithms, we implemented the following data cleaning and feature engineering steps: 
1. Eliminated duplicates (n = 12)
2. Dropped the poutcome (outcomes from previous campaign) feature as more than 86% of its values were missing
3. Eliminated the number of employees and consumer price index as we noticed values for these features had very limited data spread
4. For features with yes or no values such as "default", "housing", "loan" and "y", we converted entries to binary type after taking care of unknowns. For the "default" feature, we imputed with most frequent value and for the "housing" feature, we dropped the unknowns
5. For features with ordinal categorical values such as "education", "month" abd "day of the week", we encoded them using ordinal encoding after ensuring no unknowns in the sample
6. For the remaining categorical features "job", "marital", "contact", we leveraged one hot encoding
7. The "duration" feature was dropped as it is highly correlated with the outcome
8. Since the pdays feature included dummy 999 numerical values, we replaced these 999 values with -1 and also created a new binary feature that indicates whether a customer was contacted prior to this campaign or not

## Predictive Modeling

## Model Assessment
### Model Evaluation 

### Model Tuning 

## Findings & Recommendations 
