# TMDB Box Office Prediction

## Project Overview
This project aims to predict the worldwide box office revenue of movies using metadata from The Movie Database (TMDB). The dataset includes various attributes such as budget, release dates, genres, production companies, production countries, and more. The goal is to build a machine learning model that accurately predicts movie revenue based on these input features.

## Objective
The primary objective is to develop and evaluate predictive models to estimate a movie's revenue based on its features. The models' performance is assessed using metrics like Mean Squared Error (MSE) and R² score.

## Dataset
The dataset consists of 3,000 movies with 23 variables, including:

**Numerical Variables**: Budget, Revenue, Popularity, Runtime

**Categorical Variables**: Genre, Production Companies, Production Countries, Original Language, etc.
The dataset was sourced from Kaggle.

## Data Preprocessing
To ensure high-quality data, various cleaning and transformation techniques were applied:

## Handling Missing Values:

Columns with excessive missing values, such as belongs_to_collection and homepage, were removed.
Missing values in budget were replaced with the mean budget.

## Categorical Data Processing:

Categorical features (genres, production_companies, original_language) were transformed using one-hot encoding.
Important categorical variables were selected based on revenue impact.

## Feature Engineering:

release_date was split into release_year, release_month, and release_day to capture time-based trends.
Log Transformation was applied to budget and revenue to normalize skewed data.

## Scaling and Normalization:

Features like popularity and runtime were scaled to bring them to a comparable range.

# Exploratory Data Analysis (EDA)

## Correlation between Revenue and Budget, Popularity, Runtime 

The correlation heatmap indicates a strong positive correlation between movie budget and revenue (0.75), suggesting higher budgets often lead to higher revenues. Popularity is moderately correlated with revenue (0.46), while runtime shows a weak positive correlation with revenue (0.22), indicating less impact on earnings. These insights highlight budget as a potential key driver of a movie's financial success.

![image](https://github.com/user-attachments/assets/057690aa-1853-4254-b466-542b5b42f8ed)

## Budget vs Revenue

Both scatter plot as well as histogram shows, there is a strong relationship between revenue and budget. Revenue is highly dependent on the budget.

![image](https://github.com/user-attachments/assets/19f74608-a7ec-4c63-8a7a-589d3fe3ca5a)  ![image](https://github.com/user-attachments/assets/12009469-6b70-47b3-b3a4-ae02df9fb64c)

## Transforming Budget into Log_Budget and Revenue into Log Revenue

The budget and revenue data was transformed into a logarithmic scale to normalize the distribution and reduce skewness The original budget and revenue distribution is highly right-skewed (as we can see from the graph), indicating that most movies have a low budget, with a few outliers having very high budgets/revenue. After log transformation, the distribution appears more symmetrical and likely follows a normal distribution more closely. This transformation will improve the performance and validity of statistical analyses and regression models by meeting their assumptions of normality

![image](https://github.com/user-attachments/assets/c702ad11-05e7-4505-9248-1756aa23bc6b)! ![image](https://github.com/user-attachments/assets/ffde4fed-6807-48f2-b390-e71f586d60cb)


![image](https://github.com/user-attachments/assets/1a56cf79-57c5-47c5-8200-79b2fc0f2504) ![image](https://github.com/user-attachments/assets/6335dc51-cddd-4577-a63a-24919d1fabc7)

## Movie revenues across different original languages

The boxplots compare the distribution of movie revenues across different original languages. The left boxplot shows a wide range of revenues with many outliers, especially in English-language films. The right boxplot, which presents log-transformed revenue, reveals a more normalized view, suggesting that while there are variations in revenue across languages. We can see that there are many outliers on the higher range for English-language films. At first we thought to remove those high magnitude outliers. But then we considered the presence of those outliers reasonable, as their existence may be because of the fact that English speaking people all over the world are relatively more than other language speaking people. So to avoid any important information loss, we decided to keep those outliers as it is.

![image](https://github.com/user-attachments/assets/037eae6b-c059-458d-8c21-5d5d97e7f315)



    


## Key insights derived from data exploration:

•	Budget vs. Revenue Correlation: A strong correlation (0.75) between budget and revenue suggests that higher budgets often lead to higher box office revenue.

•	Popularity Impact: Moderate correlation (0.46) with revenue.

•	Runtime Influence: A weak positive correlation (0.22), implying that runtime has minimal impact on box office success.

•	Revenue Trends Over Time: Revenue has increased over the years, likely due to inflation, globalization, and high-budget franchises.

•	Language & Revenue: English-language films dominate, with significantly higher revenue and more variance.


# Machine Learning Models

The dataset was split into 80% training and 20% testing, and the following models were implemented:


## 1. Linear Regression
Pros: Simple and interpretable.
Cons: High MSE (4.32) and low R² (0.402), making it the weakest model.

## 2. Random Forest Regressor
Pros: Handles categorical data well, reduces overfitting.
Cons: Computationally expensive, MSE (3.78), R² (0.61).

## 3. Gradient Boosting Regressor (Best Model)
Pros: Highest accuracy with the lowest error.
Cons: Requires hyperparameter tuning.
Performance: MSE (3.43), R² (0.67).

## 4. XGBoost
Pros: Fast and efficient.
Cons: Overfitting if not tuned properly.
Performance: Slightly behind Gradient Boosting.

## Final Model Selection
After comparing all models, Gradient Boosting Regressor was chosen due to its superior accuracy and generalization ability.

![image](https://github.com/user-attachments/assets/da806e5f-9bcd-437e-b16a-54e0775f0387)


## Potential Improvements
To further refine predictions, future improvements could include:

## Better data cleaning and feature selection.
More advanced NLP techniques for analyzing cast/crew impact.
Hyperparameter tuning for all models.
Using deep learning models for better feature extraction.
