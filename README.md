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
Now that the dataset is all numerical and prepared for modeling, we split it into train/test subsets. It is important to note that our target variable is highly imbalanced which is accounted for when running the models. A test size of 20% is implemented and non boolean/non-binary features are scaled after splitting. 
First, we ran a baseline model using the most frequent class for the predicted dataset. Given that the target variable is imbalanced, simply measuring accuracry is not sufficient. We included measures of precision and recall score. Ultimately, for this type of busines problem, maximizing the recall score is of highest importance as we wouldnt want to miss potential clients that might have accepted the bank terms. 
Next, we ran classification models including logistic regression, K nearest neighbors (KNN), decision tree and SVM. Models were run with default settings with the exception of the class weight parameter that was set as balanced. 

## Model Assessment
### Model Evaluation 
Models were evaluated with respect to their train time, train accuracy, test accuracy and recall. 
Logistic regression model ran fast and was consistent in performance across train and test sets. Despite the highest recall score across models, it performed poorly when it comes to accuracy vs other models. 
KNN was fast and performed well across the board but likely overfit on training set. 
Decision tree was relatively fast but overfit the training data as training accuracy was extremely high and lower test accuracy. Both decision tree and KNN models scored very low on recall. 
SVM was very slow but performed relatively well across train, test sets  accuracy and recall. 
 
### Model Tuning 
Given that we had good starting point with the SVM and logistic regression model when it comes to the recall score, we applied GridSearchCV and tuned these models to further improve upon accuracy. The SVM model turned out to be very computationally costly and we had to limit the number of hyperparameters explored as well as limit the Kernel to liner. Ultimately, while we were able to gradually increase the recall score across the tuned model, the logistic regression model was overall our best classifier. 

## Findings & Recommendations 
Further assessing the output of our logistic regression classifier, helps inform not just which clients are most likely to accept the bank term but also features that were most predictive: 
1. The 3 mo euribor rate - Higher euribor rate (3 mo) decreases odds of client subscribing. This suggests that when interest rates are high, clients are less likely to subscribe
2. The number of days since client was last contacted - The number of days since last client was contacted has a positive coefficient suggesting that clients that werent contacted recently are more receptive to the campaign now
3. The employment variation rate - The employement variation rate is negatively correlated with likelihood of subscribing reflecting potential impact of macroeconomic conditions on client decisions
4. The consumer confidence index - When consumer conficence index rises, likelihood of subscribing increases slightly, suggesting higher confidence can mean more willingness to invest
 
 
 
 
