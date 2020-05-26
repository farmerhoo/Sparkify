# Sparkify

The graduate project of Udacity Data Mining NanoDgree

## Overview

Sparkify is an imaginary music app. The data provided are from Sparkify and include demographic information, song information, user behavior, etc. Based on the data, we used spark to clean the data, exploratory analysis, feature engineer and model to predict user churn behavior. we use spark in local mode to complete this project, but we can use this project as a starting point to extend the framework. 

In this project, we tried Logistic Regression,  Random Forest and Gradient Boosting Tree to model and predict user churn behavior. Finally, we choose the Gradient Boosting Tree as the prediction model which performs best in test data sets. Considering the unbalance of data, we choose area under ROC as the criterion. And the final model we built has a AUC of 0.642.

## Packages

- **pyspark**
- **pandas**
- **numpy**
- **matplolib**
- **datetime**

## File Structure

- mini_sparkify_event_data.json: log data of psarkify. We use this it in this project. It contains 225 distinct users.
- Sparkify-zh.ipynb: this is the python notebook file which contains all the analysis code with pyspark.
- Sparkify-zh.html: this is a HTML version of the notebook

## Project Briefs

### Extract and Clean Data

### Exploratory Data Analysis

### Feature Engineer

### Molding



## Improvement and Acknowledgement

