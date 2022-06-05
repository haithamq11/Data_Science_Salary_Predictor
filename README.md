# Data_Science_Salary_Predictor

## Data Science Salary Estimator: Project Overview
* Modified the algorithms that estimates data science salaries (MAE ~ $ 8K) to help data scientists negotiate their income when they get a job.
* Scraped over 1000 job descriptions from glassdoor using python and selenium.
* Engineered features from the text of each job description to quantify the value companies put on python, excel, aws, and spark.
* Optimized Linear, Ridge, Elastic Net, Lasso,  Support Vector, Decision Tree and Random Forest Regressors using GridsearchCV to reach the best model.

## Resources

**Python Version:** 3.7

**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium

**Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium

**Scraper Article:** https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905

**Scraping dataset by:** https://github.com/PlayingNumbers/ds_salary_proj

## Web Scraping

1000 record job postings from glassdoor.com was scraped by Ken Jee and we got the following columns:
* Job title
* Salary Estimate
* Job Description
* Rating
* Company
* Location
* Company Headquarters
* Company Size
* Company Founded Date
* Type of Ownership
* Industry
* Sector
* Revenue
* Competitors

## Data Cleaning

The data was cleaned by Ken Jee before fed to model. these are the changes as following: 

* Parsed numeric data out of salary
* Made columns for employer provided salary and hourly wages
* Removed rows without salary
* Parsed rating out of company text
* Made a new column for company state
* Added a column for if the job was at the company’s headquarters
* Transformed founded date into age of company
* Made columns for if different skills were listed in the job description:
    * Python
    * R
    * Excel
    * AWS
    * Spark
* Column for simplified job title and Seniority
* Column for description length

## Model Building

First, I transformed the categorical variables into dummy variables. I also split the data into 20% test and rest is train set.

I tried seven different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

These are the models:
**Linear Regression –** explainable method and faster to train than other machine learning models. 
**Ridge model-** less prone to overfitting and interpretable.
**Lasso model-** can handle high-dimensional data and no need for feature selection.
**ElasticNet model-** This gives us the benefits of both Lasso and Ridge regression. It has been found to have predictive power better than Lasso, while still performing feature selection.

**Support Vector Regressor model-** SVR is robust to the outliers. SVR performs lower computation compared to other regression techniques.
**Decision Tree Regressor model-** explainable and interpretable.
**Random Forest Regressor model-** reduces overfitting and higher accuracy compared to other models.

## Model performance

The Decision Tree model far outperformed the other approaches on the test and validation sets.

**Decision Tree Regressor model:** MAE = 8.3
**Support Vector Regressor model:** MAE = 10.62
**Random Forest Regressor model:** MAE = 11.72
**Linear Regression:** MAE = 18.83 
**Ridge model:** MAE = 19.44
**Lasso model:** MAE = 19.44
**ElasticNet model:** MAE = 25.35
