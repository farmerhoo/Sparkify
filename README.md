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

In this part, we get the following information or do the following actions:

1. Data Size: $ 286500 \times 18$
2. The data contains following columns and brief introduction of each column:

- Numerical Data：
  - userId(string): the unique user ID
  - ts(long): time stamp
  - sessionId(long): get an unique session ID when opening app each time
  - length(double): the time length
  - itemInSession(long): number of items in each session
  - registration(long): the time stamp of registration
- Category Data：
  - artist(string): artist of music
  - auth(string): user authentication status
  - firstName(string): user firstname
  - gender(string): user gender
  - lastName(string): user lastname
  - level(string): user level, has free and paid two types
  - location(string): user location
  - method(string): has put and get two types
  - page(string): page name，has Home, Upgrade, Downgrade etc
  - song(string): song
  - status(long): request status，contains 200、307、404
  - userAgent(string): user agent

3. Cleaning data and drop missing data in the columns about the information of songs

### Exploratory Data Analysis

- Define customer churn data
    - Define churn column, 1 represent user clicked "Cancellation Confirmation" page.
    - Define phase column, By defining this column, we understand what a "Cancellation Confirmation" page is and what a churned user is: the user who leave Sparkify and do not return。
- Exploring single variable
    - There are a total of 225 unique users in this data set, and the proportion of churned users is 23.11%
    - In this data set, the user ID with the most interactions on the software is 39
    - The number of user interactions in this data set is in the long tail distribution, and most of the user interactions are below 2000
    - The number of artists included in this dataset is 17,656
    - The number of songs included in this dataset is 58481
    - Kings Of Leon is the artist with the highest play volume Of this data set
    - The most played song in this data set is You're The One, and I often listen to The second ranked Undo also.
    - Most users in this dataset are Logged in
    - The users of this data set are slightly more male than female
    - Most users of this data set operate in the paid state, indicating that the payment rate of the software is relatively high
    - The top three cities in software usage in this data set are Los Angeles, New York and Boston
    - The most visited page in this data set is Next Song page, followed by Thumbs Up thumb Up page, and then Home page and Home page
    - There are 252 requests from users in this dataset that return 404, and there may be pages that need to be partially fixed
    - This dataset contains user interaction data from October 1, 2018 to December 31, 2018
- Explore Multi-variables
    - The number of artists that churned users listened to was relatively small
    - The number of songs that churned users was relatively small
    - The number of churned users adding songs to playlists is relatively small
    - The number of churned users adding friends is relatively small
    - The number of churned user interactions is relatively small
    - The number of churned users opening the app is relatively less
    - The number of churned users is significantly shorter
    - The proportion of retained users is similar between men and women, while the number of churned users is slightly more male than female
    - The churn rate of paid users was slightly lower, indicating that paid users were more likely to recognize the product, or pay because the product was recognized.
    - The number of users of the APP hit a small peak between 14:00 and 16:00

### Feature Engineer

- numerical features
  - Number of songs(NumSongs): clicking NextSong every time means listening to one song
  - Number of PlayList songs(numInList) : clicking Add to PlayList one song means add one song to playlist
  - Add friends(numFriends): consider adding one Friend per click on Add Friend
  - Number of app opening(numSession) : a new sessionId is considered to mean opening the app once
  - Registration days (regDay) : the number of days from the registration time to the record that the app was last opened
- category features
  - gender
  - level
  - location: because the location format is generally "locPart1, locPart2", so it is divided into two parts
    - Location front part (locPart1)
    - Location latter part (locPart1)

### Molding

- Logistic Regression
- Random Forest
- Gradient Boosting Tree
- model selection

## Improvement and Acknowledgement

The performance of the model may also be optimized by continuing to optimize feature engineering and hyper parameters. Thanks Udacity for giving me the chance to get started with data mining. 