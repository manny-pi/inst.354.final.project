# INST354 Final Report

**Team 8**: Emily Baelis, Noah Ramey, Octavio Sanchez, Prince Okpoziakpo

## Introduction

1. Introduction: Give the details on the source of your data, its content, and some questions you are interested in

For our project, we have set out to analyze a dataset that contains information about earnings for Data Science professionals. Our goal is to determine if we can use features in the dataset to predict the *job title* of an employee.

We'll be using the [Data Science Salaries 2023 💸](https://www.kaggle.com/datasets/arnabchaki/data-science-salaries-2023) dataset, which we collected from Kaggle. The dataset is 3755 rows by 11 columns, and the features are various demographic information about different positions in the field of Data Science. The dataset consists of *numeric* and *categorical* variables, which are listed below:

### **Numerical Variables**

* **work_year**: The year the salary was paid.
* **salary**: The total gross salary amount paid.
* **salary_in_usd**: The salary in USD
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

For our model, we decided to use the four numerical features to help determine the job title of an employee: **remote_ratio**, **salary_in_usd**, **employee_residence**, and **company_size**. For practical reasons, we thought that encoding categorical variables as features would be a unique challenge, and we believe the residence of the employee and company size would have an impact on what career they would have (proximity to DC may imply working for a contractor, for example, which could skew results to their data needs).

We chose the **remote_ratio** variable because we think it would be useful in answering questions about patterns in the job market based on location (e.g., Do some jobs demand more on-site work? Is this the case for Data Engineers/Scientists?). We chose the **salary_in_usd** variable as our intuition leads us to believe that similar jobs will have similar pay, making this variable a good predictor of job title. We chose the **employee_residence** variable becuase we believe that there is a correlation between location and job title, as companies in different locations might different needs. Finally, we chose the **company_size** because we believe the size of a company would dictate the Data Science it would need.

The dataset list 93 unique job titles, but the preliminary data analysis revealed that the two most common job title's, by a wide margin, are "Data Scientist", and "Data Engineer"; 50% of all careers in the dataset are made of these two careers. Because of this, we have encoded the job title target column as `1` for Data Scientists/Engineers, and `0` for any other data related career.

## Data Preprocessing

3. Split the data into train and test data. Preprocess the data using the StandardScaler.

. . .

## Model Training and Testing

4. Use scikit-learn Logistic Regression for training and testing your model.

. . .

## Model Evaluation

5. Use the classification report and explain the results: Precision, Recall, and F1-score.

The Precision of Data scientists/engineers and other data job titles are .56 and .50 respectively, meaning: 56% of predicted Data engineer/scientists are truly data engineers/scientists, and 50% of predicted alternate job titles in the field happen to truly fit that characterization.

The Precision of Data scientists/engineers and other data job titles are .56 and .50 respectively, meaning: 33% of actual Data scientists/engineers are predicted as positive, while 72% of alternate job titles in the field are predicted as positive

The F1-Score for Data engineer/scientists and alternate titles at .42 and .59 respectively, meaning, similarly to the precision and recall scores, that the model is not very good at making classifications as currently constructed. This makes sense, since it is the harmonic mean of both recall and precision. So it would be higher for alternate job titles since those scores have a higher average.

This model, as it currently stands, has a good bit of room to grow before we would feel confident in making classifications about peoples jobs, as evidenced by the report metrics. More data, and perhaps more useful features to build models on (perhaps more demographic information, Cost of living, raw text reviews of employees job satisfaction, etc) would lead to a more successful model, though the exact improvements are currently unknown.

## Confusion Matrix

6. Plot the Confusion Matrix and explain the output

The confusion matrix below provides a visual representation of the report we derived from training our logistic regression model. The matrix provides us with a look into the exact numbers of classifications, broken down into true positives/negatives, and false positives/negatives.

For example, 327 of the (327 + 164) = 491 Data scientist/engineers in the test set were incorrectly predicted as 'other data career' (False negative). 164 of the 291 predicted data scientist/engineers were correctly classified (True positives, ratio indicative of precision.)

## Splitting Data by Country

7. Split the data according to a demographic variable (gender, ethnicity, age, religion etc.) and go through the steps (4) , (5) and (6) for each category, e.g., old vs young or male vs female.

## Implications on Fairness in AI Decision-Making

8. Explain the results of (7) in terms of fairness in AI decision-making: are there differences
among the groups in terms of precision, recall, or the false positive rates?

* Companies can determine how to compensate their employees.
* Employees can figure out what to expect from cpanies, compensation wise.
* Countries can deetermine what sectors are struggling, thriving; how to help the industry grow.