---
title: Final Project
draft: false
tags:
---

## Prerequisites

1. [[Projects Folder/Machine Learning/Classification Trees]]
2. [[Projects Folder/Machine Learning/Decision Trees]]
3. [[Projects Folder/Machine Learning/Bias vs Variance]]
4. [[Projects Folder/Machine Learning/Encoding]]
5. [[Projects Folder/Machine Learning/Random Forest]]
6. [[Projects Folder/Machine Learning/AdaBoost]]
7. [[Projects Folder/Machine Learning/Gradient Boost]]
8. [[Cosine Similarity]]
9. [[CatBoost]]

## Goal

In this project, I aimed to predict customer churn for a telecommunications company using a dataset from Kaggle. 

My goal was to understand why customers leave and to create a machine learning model that can predict which customers are at risk of churning. 

This project showcases how machine learning can address real-world challenges.

Original Kaggle Competition: [Link](https://www.kaggle.com/datasets/blastchar/telco-customer-churn/code)

## Dataset

| Features         | Description                                                                                           |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| customerID       | Customer ID                                                                                           |
| gender           | Male/Female                                                                                           |
| SeniorCitizen    | Whether the customer is a senior citizen or not (1, 0)                                                |
| Partner          | Whether the customer has a partner or not (Yes, No)                                                   |
| Dependents       | Whether the customer has dependents or not (Yes, No)                                                  |
| tenure           | Number of months the customer has stayed with the company                                             |
| PhoneService     | Whether the customer has a phone service or not (Yes, No)                                             |
| MultipleLines    | Whether the customer has multiple lines or not (Yes, No, No phone service)                            |
| InternetService  | Customer’s internet service provider (DSL, Fiber optic, No)                                           |
| OnlineSecurity   | Whether the customer has online security or not (Yes, No, No internet service)                        |
| OnlineBackup     | Whether the customer has online backup or not (Yes, No, No internet service)                          |
| DeviceProtection | Whether the customer has device protection or not (Yes, No, No internet service)                      |
| TechSupport      | Whether the customer has tech support or not (Yes, No, No internet service)                           |
| StreamingTV      | Whether the customer has streaming TV or not (Yes, No, No internet service)                           |
| StreamingMovies  | Whether the customer has streaming movies or not (Yes, No, No internet service)                       |
| Contract         | The contract term of the customer (Month-to-month, One year, Two year)                                |
| PaperlessBilling | Whether the customer has paperless billing or not (Yes, No)                                           |
| PaymentMethod    | The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card |
| MonthlyCharges   | The amount charged to the customer monthly                                                            |
| TotalCharges     | The total amount charged to the customer                                                              |
| Churn            | Whether the customer churned or not (Yes or No)                                                       |

### Step 1: Importing my libraries

#### Explanation
The 1st step in this project is to import the necessary libraries in order to perform my testing. This include the machine learning scikit-learn module along with pandas for handling data and numpy for basic math operations.

As the dataset has a high number of discrete features (Features with categories rather than numbers), I will be suing the CatBoost algorithm for my machine learning prediction [[CatBoost]]

I will be coding in python for this project:

#### Code

```python
import numpy as np

import pandas as pd

import os


from sklearn import metrics

from sklearn.model_selection import train_test_split, StratifiedShuffleSplit

from sklearn.metrics import (

    accuracy_score, classification_report, recall_score, confusion_matrix,

    roc_auc_score, precision_score, f1_score, roc_curve, auc

)

from sklearn.preprocessing import OrdinalEncoder


from catboost import CatBoostClassifier, Pool
```

### Step 2: Loading in the dataset and Data Preprocessing

#### Explanation
Next I will read in the dataset which is currently stored as a csv folder in my main projects folder.

Once this is loaded in, I will perform the following data reprocessing to ensure that all missing values are handled and the typing of all columns is correct:

1. Convert the Total Charges column to be numeric
2. Fill in all rows with a missing 'Total Charges' to be equal to tenure (amount of time with the company) x monthly charge (the customers average monthly charge)
3. Convert the senior citizen type to object
4. Convert multiple lines where a sentences are used to describe the service to plain yes or no's
5. Set Churn to be 1 or 0 as yes or no

Data pre-processing is one of the most, if not the most important aspect of machine learning projects. In reality, most datasets provided are not clean and ready for modelling straight away and therefore have to go through multiple analysis as well as pre-processing and cleaning before ready for use I am still a beginner and therefore have applied minimal data pre-processing techniques apart from what was completed in the main project

#### Code:

```python
data_path = "churn_data.csv"

df = pd.read_csv(data_path)


# Convert TotalCharges to numeric, filling NaN values

df['TotalCharges'] = pd.to_numeric(df['TotalCharges'], errors='coerce')

df['TotalCharges'].fillna(df['tenure'] * df['MonthlyCharges'], inplace=True)


# Convert SeniorCitizen to object

df['SeniorCitizen'] = df['SeniorCitizen'].astype(object)


# Replace 'No phone service' and 'No internet service' with 'No' for certain columns

df['MultipleLines'] = df['MultipleLines'].replace('No phone service', 'No')

columns_to_replace = ['OnlineSecurity', 'OnlineBackup', 'DeviceProtection', 'TechSupport', 'StreamingTV', 'StreamingMovies']

for column in columns_to_replace:

    df[column] = df[column].replace('No internet service', 'No')


# Convert 'Churn' categorical variable to numeric

df['Churn'] = df['Churn'].replace({'No': 0, 'Yes': 1})

```


#### Step 3: Creation of Training and Testing Datasets

#### Explanation
In machine learning, it is common practice to split your dataset between a testing and training dataset. The training dataset, as the name implies, is udes to create the model . The testing dataset is the used to test the accuracy of the model. 

In this project, we will use a 20:80 split between the testing and training dataset. The split is not completely random as we will apply stratification. This is to ensure that there is equal representation of the the customers across both the training and testing set.

Each dataset is split into an x and a y set. The x set will consist of all the features (columns) aside from the value we are trying to predict (the target) whilst the y will be the target (column) we are predicting

#### Code

```python
# Create the StratifiedShuffleSplit object

strat_split = StratifiedShuffleSplit(n_splits=1, test_size=0.2, random_state=64)

train_index, test_index = next(strat_split.split(df, df["Churn"]))


# Create train and test sets

strat_train_set = df.loc[train_index]

strat_test_set = df.loc[test_index]


X_train = strat_train_set.drop("Churn", axis=1)

y_train = strat_train_set["Churn"].copy()


X_test = strat_test_set.drop("Churn", axis=1)

y_test = strat_test_set["Churn"].copy()
```

### Step 4: Making the Model

#### Explanation
Now that we have our datasets, we will need to create our model using the training dataset. 

We will first need to let the CatBoost algorithm know which features are categorical so these can be encoded first. Detailed explanation of encoding [[Encoding|Detailed Explanation of Encoding]].

#### Code
```python
# Identify categorical columns

categorical_columns = df.select_dtypes(include=['object']).columns.tolist()

  

# Initialize and fit CatBoostClassifier

cat_model = CatBoostClassifier(verbose=False, random_state=0, scale_pos_weight=3)

cat_model.fit(X_train, y_train, cat_features=categorical_columns, eval_set=(X_test, y_test))

  
# Predict on test set

y_pred = cat_model.predict(X_test)
```

### Step 5: Evaluation of Model

The last step in this process is to evaluate the success of the model. Thew scikit-learn library has a function to automatically calculate the success of our model. This is done below in the code.

An accuracy of 0.7764 was achieved in this model.

#### Code
```python
# Calculate evaluation metrics

accuracy, recall, roc_auc, precision = [round(metric(y_test, y_pred), 4) for metric in [accuracy_score, recall_score, roc_auc_score, precision_score]]

# Print results

print(result)
```

Yay, we are done and can save this model to use in any future evaluations of churn. For example, this model could be used to identify customers at risk of deactivating their accounts and specific marketing strategies could be tailored towards these individuals so the business does not lose their exisitng customer base.