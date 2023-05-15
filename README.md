# INST354 Final Report

**Team 8**: Emily Baelis, Noah Ramey, Octavio Sanchez, Prince Okpoziakpo

## Introduction

1. Introduction: Give the details on the source of your data, its content, and some questions you are interested in

For our project, we have set out to analyze a dataset that contains information about earnings for Data Science professionals. Our goal is to determine if we can use features in the dataset to predict the *job title* of an employee.

We'll be using the [Data Science Salaries 2023 💸](https://www.kaggle.com/datasets/arnabchaki/data-science-salaries-2023) dataset, which we collected from Kaggle. The dataset is 3755 rows by 11 columns, and the features are various demographic information about different positions in the field of Data Science. The dataset consists of *numeric* and *categorical* variables, which are listed below:

### **Numerical Variables**

* **work_year**: The year the salary was paid.
* **salary**: The total gross salary amount paid.
* **salaryinusd**: The salary in USD
* **remote_ratio**: The overall amount of work done remotely

### **Categorical Variables**

* **job_title**: The role worked in during the year.
* **experience_level**: The experience level in the job during the year
* **employment_type**: The type of employment for the role
* **salary_currency**: The currency of the salary paid as an ISO 4217 currency code.
* **employee_residence**: Employee's primary country of residence in during the work year as an ISO 3166 country code.
* **company_location**: The country of the employer's main office or contracting branch
* **company_size**: The median number of people that worked for the company during the year

## Data Cleaning

2. Prepare and wrangle your data. Explain how/why/which variables you selected and justify
dropping/dealing with null values

For our model, we decided to use the four numerical features to help determine the job title of an employee: **work_year**, **salary**, **salaryinusd**, and **remote_ratio**. For practical reasons, we thought that encoding categorical variables as features would be a unique challenge, and we believe the residence of the employee and company size would have an impact on what career they would have (proximity to DC may imply working for a contractor, for example, which could skew results to their data needs).

Remote_ratio was an interesting feature as well, as we found it would be interesting to see if it makes a major impact on patterns in jobs. (Do some jobs demand more on-site work? is this the case for Data Engineers/Scientists?)

Another Numerical feature we chose was salary in USD. We saw no reason to use other salary features on the chance it may negatively impact our model when we already can control for currency differences with this feature.

The dataset list 93 unique job titles, but the preliminary data analysis revealed that the two most common job title's, by a wide margin, are "Data Scientist", and "Data Engineer." Because of this, we have encoded the job title target column as 1 for data scientists/ engineers, and 0 for any other data related career. Below is our work at processing our data and building a classifier that would help us to predict this target variable.

``` Python
if x > 10: 
    print('so bored :/')
else: 
    print('lit party dude! \__d(- _ -)b__/')
```

## Data Preprocessing

3. Split the data into train and test data. Preprocess the data using the StandardScaler.



## Model Training and Testing

4. Use scikit-learn Logistic Regression for training and testing your model.

## Model Evaluation

5. Use the classification report and explain the results: Precision, Recall, and F1-score.

## Confusion Matrix

6. Plot the Confusion Matrix and explain the output

## Splitting Data by Country

7. Split the data according to a demographic variable (gender, ethnicity, age, religion etc.) and go through the steps (4) , (5) and (6) for each category, e.g., old vs young or male vs female.

## Implications on Fairness in AI Decision-Making

8. Explain the results of (7) in terms of fairness in AI decision-making: are there differences
among the groups in terms of precision, recall, or the false positive rates?
[2 points]