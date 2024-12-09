# SYRIATEL CUSTOMER CHURN
Author: Augustine Komen

## Overview
This project applies machine learning techniques to develop a model aimed at identifying customers who are at risk of discontinuing their subscription with Syriatel. The dataset, sourced from Kaggle, comprises 20 variables capturing customer behaviors and service usage patterns, including a total of 3,333 records. Within this dataset, 483 entries represent churned customers, while the remaining 2,850 correspond to retained customers. Classification algorithms are employed to predict the "churn" variable, with recall as the primary evaluation metric. Among the models explored, a decision tree refined through hyperparameter tuning emerges as the most accurate.

## Business Understanding
In the telecommunications sector, customer churn presents a significant challenge. It refers to the phenomenon where customers terminate their subscription or cease engaging with a company’s services. Churn can stem from various factors, such as better pricing or service offerings from competitors, dissatisfaction with customer support, or poor engagement.

For Syriatel, a leading telecommunications provider in Damascus, Syria, maintaining customer loyalty is critical. The company offers services such as voice calls, SMS, GSM, and internet, with a strong focus on customer satisfaction. Retaining existing customers is more cost-efficient than acquiring new ones. This project aims to identify at-risk customers and the primary factors driving churn, enabling Syriatel to proactively address churn and strengthen customer retention strategies.

## Objectives
1. Develop a predictive model for identifying customers likely to churn.
2. Identify the most influential factors contributing to customer churn.
3. Provide actionable recommendations for reducing churn based on model insights.

## Data Understanding
The dataset exhibits class imbalance, with 85.51% of customers labeled as "retained" and 14.49% as "churned."
![Class Imbalance](classimbalance.png)
The dataframe has both continuous and categorical variables.


Scaling varies among the features, and some of them do not exhibit a normal distribution. Consequently, it is necessary to perform both scaling and normalization on the features.
![Distribution](distribution.png)
Most features exhibit a notably weak correlation with each other. Nonetheless, a perfect positive correlation is observed between specific pairs of variables: total evening charge and total evening minutes, total day charge and total day minutes, total night charge and total night minutes, and total international charge and total international minutes. This correlation is anticipated since the charge of a call is inherently influenced by the call's duration in minutes. To address multicollinearity, it will be necessary to eliminate one variable from each correlated pair.
![Correlation](corr.png)

## Data Preparation for Machine Learning
- **Handling Multicollinearity**: Features like total charges are removed to avoid duplication of information.
- **Data Splitting**: The dataset is divided into training and testing subsets.
- **Encoding Categorical Data**: Dummy variables are created for categorical attributes.
- **Addressing Class Imbalance**: The minority class is oversampled using the SMOTE technique to ensure balanced representation.

### Modelling
Three models are tested:

    1. Logistic Regression (baseline model)
    2. Decision Tree
    3. Decision Tree (with hyperparameter tuning)

### Evaluation
The decision tree model with fine-tuned hyperparameters exhibits superior performance, boasting the highest recall score, with accuracy and precision scores surpassing the mean values.
However, it's worth noting that the achieved recall score falls slightly below the set threshold of at least 85%.
Below, you can find the feature importance of this top-performing model.
![Top performing features](evaluation.png)

## Conclusions
* The chosen model for predicting customer churn is the decision tree with fine-tuned hyperparameters, boasting the lowest count of false negatives.


* Key features crucial for forecasting customer churn are:

    - `Total Day Minutes:` Reflects the cumulative minutes spent by the customer on daytime calls.

    - `Total Evening Minutes:` Sums up the minutes spent on evening calls by the customer.

    - `Customer Service Calls:` Indicates the number of calls the customer has initiated to reach customer service.

## Recommendation
1. **Customer Service Strategy:** Syriatel should ensure a robust customer service strategy to meet customer expectations effectively and assess customer interactions. This includes tracking and addressing both positive and negative feedback from customers.
 
2. **Resolve Customer Issues:** Since customer service calls have the highest correlation with churn, implying that the more times a customer initiates a call to reach customer service, the more likely they are to churn. Syriatel should ensure that issues raised by clients who call are resolved promptly and efficiently.

3. **Call Charge Rates:** Given that total day and night minutes are key factors for predicting churn, Syriatel should assess its call charge rates in comparison to competitors. Lowering the charges per minute for calls could prove instrumental in retaining customers and preventing churn.

## Next Steps
- Deploy the model for real-time customer churn prediction
- To further refine the model and overcome challenges like overfitting, additional data collection is essential. This could include
gathering data on customer satisfaction, competitor pricing, and service quality metrics. Deploying the model into a live environment will also provide valuable feedback for continuous improvement.# Phase-3-Project-Syriatel-Customer-Churn
