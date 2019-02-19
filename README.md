# Tabular Data Walkthrough

!(https://bloximages.chicago2.vip.townnews.com/theoaklandpress.com/content/tncms/assets/v3/editorial/0/49/0491e2f9-1928-57ae-99df-4534f2bc924f/5b58983fd1c37.image.jpg?resize=1700%2C1118)

## Summary

The following is a brief write-up of the process to come up with a model for predicting how many meals will be ordered by 
using data related to features involving users and meals. *Note: More details can be found in the attached Jupyter Notebook 
containing code, explanations, and justifications for the decisions that were made.

My plan was to "do data science" by way of investigating the problem and performing exploratory data analysis, data cleaning, 
feature engineering, building a model, and interpreting the results.

After removing outliers, creating dummy variables, engineering features, and pre-processing data, I tried the following 
classification algorithms: logistic regression, nearest neighbors, random forest, and a deep neural network.

## Data

4 input files:

* meal_features - Data containing features related to various meals
* meals_seen - Data containing information on meals previously seen by users
* meals_sent - Data containing the meals to be sent out the following day
* user_features - Data containing various information on user features

## Analysis

The neural network showed the lowest cross-entropy loss (about 0.31 compared to the baseline of of 0.38) on the validation set 
and it’s predictions were well-calibrated, so I used the probabilities from its predictions as the basis for estimating how 
many meals were to be ordered. However, when I applied it to the ‘meals to be sent’ dataset, I noticed a dramatic 
inconsistency in the predictions. I concluded this had to be due to the differences between the labeled data and the 
“meals to be sent” data, so I provided a quick adjustment of the some of the predictions to bring them in line with 
expectations. I also included an upper prediction interval, since it seemed relevant to the problem.

In the end, I determined that there were too many “issues” with the data to use the algorithm as-is, and recommended a 
different strategy using hypothetically collected data containing a time-series of records for each day across multiple 
subscription cycles.
