# Sentiment Analysis on BISA AI Android App

* Written by Yohanes Setiawan
* This is my final project from MasterClass and On the Job Training: Data Science Intensive Batch 14, BISA AI Academy 2022
* For further reading of the code, please open the `.ipynb` file

# **Business Understanding**

## Introduction

* BISA AI is an Indonesian start-up which provides products and services of Artificial Intelligence (AI) starting from 2019
* BISA AI also has BISA AI Academy as an education platform for Data Science and Full Stack Programming
* BISA AI Academy has its own Android application which can be downloaded through Google Play which provides several free courses

## Problem Statement
BISA AI wants to evaluate performance of its Android application 

## Goal
To give feedbacks to BISA AI about BISA AI Academy's Android application for better future performance

## Research Questions
* How to make sentiment analysis for BISA AI Academy application?
* How to evaluate the result of sentiment analysis for BISA AI Academy application?

## Objective Statements
* Designing sentiment analysis for BISA AI Academy application
* Get insights from the result of sentiment analysis for BISA AI Academy

# **Analytical Approach**

* Descriptive analysis
* Graph analysis
* Table analysis
* Sentiment analysis

# **Data Understanding**

* The dataset is about user reviews toward BISA AI application on Playstore

![](https://drive.google.com/uc?export=view&id=1tZCM6rYBNh7UBM3f9emnxEwU9j_4-Eny) </br>

* The dataset is still not clean and need further pre-processing steps for cleaning data

# **Data Cleaning**

## Selecting appropriate columns
* Selected column: `App Version Name`, `Review Last Update Date and Time`, `Star Rating`, `Review Text`, and  `Developer Reply Text`

## Checking and Handling Missing Values
![](https://drive.google.com/uc?export=view&id=1IJ3o90VV2vbLTama-JJkiiU7MAcJC4wv) </br>
* Removing 55 missing in `Star Rating` rows
* Imputing the missing value in `App Version Name` with after Non-Missing Values
* Imputing the missing value in `Review Text` and `Developer Reply Text` with `None`

## Checking and Handling Duplicated Data
![](https://drive.google.com/uc?export=view&id=1845SyxpCfuWKyMoeK52TzRxEagWu7D26) </br>
* Therefore, there is no duplicated data in the dataset

## Text Pre-processing

### Case Folding and Removing
![](https://drive.google.com/uc?export=view&id=1JIZrVBZumFPLnJ6ZYyJfhjD4cRGTv9mH) </br>
* Lowering the string case
* Removing punctuation(s)
* Removing whitespace
* Removing special character(s)

### Tokenization
* Used method: Word tokenization

### Spelling Check and Correction
![](https://drive.google.com/uc?export=view&id=1aaObMd1-zlL3zq7o-8tQGzce01q3pnbo) </br>

* Checking and comparing words from KBBI (Indonesian Dictionary)
* Saving the different words as “not_found”

![](https://drive.google.com/uc?export=view&id=1oiDt5EVgk4brkbb2Yd53jW0G0ViCgw18) </br>

* Making my own slang dictionary
* Matching every word with the “not_found” text file
* Converting slang words into common words

### Stopword Removal and Stemming
![](https://drive.google.com/uc?export=view&id=164BQCYH10IFqtoBtZUtXSXBVPIXHRAdJ) </br>

* I used Sastrawi (library of NLP for Bahasa Indonesia) to list the stopword and did stemming
* Also, I created my own “stopword_add” list

### Spelling & Stopword Iteration
![](https://drive.google.com/uc?export=view&id=1luRfOsJN77bnDiyhaFW36_GyLxYvPAkI) </br>

* I iterated spelling check and stopword removal for better cleaned text data
* Finally, I saved the cleaned data for Exploratory Data Analysis (EDA) and predictive modelling

# **Exploratory Data Analysis (EDA)**

## Descriptive Statistics
![](https://drive.google.com/uc?export=view&id=1BQDl1NeVtHJJsQhV8cDqMToXUL43D5Ho) </br>
![](https://drive.google.com/uc?export=view&id=11-bF5MgPIzMjj1-4q2uy2uPBJ4Aphzva) </br>
* The average of rating is 4.7 which is quite good for BISA AI application
* Lower std (standard deviation) of rating  (closer to zero) makes the average is representative to the central of the dataset
* There are too many missing reviews in the dataset that I need to handle for sentiment prediction
* Also, most of reviews are not replied by the admin

## Get Insights

### How is app version name and review last update in date and time related to star rating?
![](https://drive.google.com/uc?export=view&id=1uD0Vx7B7TaOf5Cpj_Zb__4JzToNZXo_p) </br>
* The lowest rating occurs on version 2005.0 (< 4.0)
* The highest rating occurs on version 2004.0 (close to 5.0)

### Why has BISA AI app version 2005 been the lowest rating score?
![](https://drive.google.com/uc?export=view&id=1-nkl56K0mOnSr3zdaRJkSdtAcTWzI7i5) </br>
* More than 40% people voted below 4.0 for this version
* From the WordCloud, I can find: "video", "teks, "materi", "tiba-tiba", "bug", "hitam" means there are technical problems occur in this version, such that bug like black screen while video and material are opening. Also, somehow the application is crashed suddenly on the phone

### How is percentage for each star rating for user with text review?
![](https://drive.google.com/uc?export=view&id=1k3gGz-aHK6fgjrjGoKvkWc9dBBNO9NxV) </br>
* This is for users who fills the text reviews (either Bahasa Indonesia or English)
* More than 90% users gives rating 4 or 5 to this application
* Less than 5% users gives lower rating or not many people are disappointed with BISA AI application

### How is percentage for each star rating for user with empty text review?
![](https://drive.google.com/uc?export=view&id=1aIpzZlaC9qP1vs1FzWkLpRGSLk20nIYI) </br>
* This is for users who did not fill the text reviews (only gives rating)
* Similar with users with text reviews, more than 90% users like this application with rating 5 or 4
* Less than 5% users dislike this application
* There is no user in this empty text reviews who give rating 3

### What is the most frequent words for non-empty text reviews?
![](https://drive.google.com/uc?export=view&id=1o10hDavIjU2Yg8emJqonj9F7QP3iJxeY) </br>
* Aplikasi", "kursus", "bagus", "ai", "ajar", "materi", "bantu", "menarik", "keren" has been top comments for BISA AI application (in English: "application", "course", "good", "ai", "learn/learning", "material", "helpful", "interesting", "cool")
* Most of users are interested in BISA AI application through its courses and learning materials
* Most of users learn AI (Artificial Intelligence) and Data Science through this application

### What are top 10 most frequent words for each star rating?
![](https://drive.google.com/uc?export=view&id=13u0YlJGtXbzyApTEsy3f05B5a2CO_jFn) </br>
* (English): "application", "learn/learning", "ai/artificial intelligence", "good", "easy", "material", "helpful", "course", "smiling_face", "thank you“
* Based on users who gives rating=5.0, they feel blessed with the existence of BISA AI application which is helpful, easy to learn, and provide many courses
* Furthermore, most of people who downloaded this app want to learn AI (Artificial Intelligence)

![](https://drive.google.com/uc?export=view&id=1z8mDYMZBVwARmK5ScOw48vyWB3EKxdjW) </br>
* (English): "course", "material", "good", "application", "suggestion/advice", "learning/learn", "repeat", "quiz", "less", "feature“
* Based on users who gives rating=4.0, most of words are positive words like users who gives rating=5.0
* In addition, there are some complaints and suggestions: the quizzes can not be repeated and less features given from the application


![](https://drive.google.com/uc?export=view&id=18juNJy2TB2fg91zNmtZGyO11ll9uVftD) </br>
* (English): "course", "enter/login", "register", "error", "repeat", "login", "repeat", "menu", "list", "data", "material“
* Based on users who gives rating=3.0, I start to find complaints start from this rate
* Most of users complaint of login and register error from BISA AI application
* Most of users complain of difficulties in entering their data to the application


![](https://drive.google.com/uc?export=view&id=1jp6_Ozt3gM-GFOMg1WsdYD3Qjpl4YF53) </br>
* (English): "material", "video", "syllabus", "lost", "text", "suddenly", "problem", "quiz", "grey", "true“
* Based on users who gives rating=2.0, many complaints are found
* Users are complaining about sudden lost of text and video from material in BISA AI application
* Users are complaining about "grey area" in the true answers of the quiz problems which led to double true answers in multiple choices from quiz


![](https://drive.google.com/uc?export=view&id=1pCvlchNiXftusEORWlk-arTHt25h9f5P) </br>
* (English): "material", "course", "mentor", "reply", "good", "time", "clear", "application", "sorry", "download“
* Based on users who gives rating=1.0, I found a new critic compared to users who gives rating=2.0
* There are users who contacted the mentor but did not receive a reply from the mentor which makes them feel regret of downloading BISA AI application

# **Feature Engineering**
* Multiclass classification for sentiment analysis: Negative (-1), Neutral (0), and Positive (1)
* Negative (rating 1-2), Neutral (rating 3), and Positive (rating 4-5)

# **Data Preparation**

## Train Test Split
![](https://drive.google.com/uc?export=view&id=17z6OBBOHjSbnKsWSVs7Wd9uHYWSnxSkz) </br>
* 70% training data, 30% testing data
* I cannot use accuracy as the main metric because of severe imbalanced class in this dataset

## Feature Extraction and Scaling
* I used TF-IDF Vectorizer to convert the text data into numerical data
* TF-IDF quantifies words in a set of documents
* Feature scaling is done by StandardScaler() 

# **Modelling**
* I focus on recall from non positive class (-1 or 0) to give evaluation for BISA AI Application
* Furthermore, I check the confusion matrix

Machine Learning Models:
* Naive Bayes
* Random Forest
* Gradient Boosting Trees
* Support Vector Machine

## Naive Bayes
![](https://drive.google.com/uc?export=view&id=1vf0guhjW-hqtAlJj8ZjH3CNdbstkHyGs) </br>

![](https://drive.google.com/uc?export=view&id=1RYOPUgN8tvoQfPblGwh2gPAfliiTaIzo) </br>

## Random Forest
![](https://drive.google.com/uc?export=view&id=1cmtKn11XgHck6HXI7ZlSE0Pucwjg2GW6) </br>

![](https://drive.google.com/uc?export=view&id=1Xw40hdZr_Bn3JjMcP5XtJi-kHjdw78tJ) </br>

## Gradient Boosting Trees
![](https://drive.google.com/uc?export=view&id=1NDapiKzYkP8vVy74T9DQbNfc-ukp_eqJ) </br>

![](https://drive.google.com/uc?export=view&id=1IG349lTzdrHAGz6ZZzHaHu23yttrqFzr) </br>

## Support Vector Machine
![](https://drive.google.com/uc?export=view&id=1Y5AUBxH2NbHrSYc4i6eLGh0-Zg_uifSO) </br>

![](https://drive.google.com/uc?export=view&id=1vFyoriB_y9kUKXBDq3WB7wiLufv6ekCm) </br>

# **Model Selection**
![](https://drive.google.com/uc?export=view&id=16wnEXl7mEbPeix55GbYRoUOgbJu17IUO) </br>
* Based on its higher recall from negative and neutral, I choose Naive Bayes Classifier as our sentiment prediction model which can be deployed in the future.

![](https://drive.google.com/uc?export=view&id=19dsT_Wfszl6LkCOE46r3ecyqvJZJCW3R) </br>

# **Summary of Findings and Suggestions**
* Most of people like BISA AI Application as a free and an easy-to-use AI (Artificial Intelligence) education platform in Bahasa Indonesia
* Technical complaints: black screen, difficult to login/register, error to open video/text materials
* Non technical complaints (material): grey area of quizzes  
* Suggestion for the technical complaints: BISA AI should keep maintaining the application and give an opportunity to the users to explain more details about their complaints with give them reply, as I identified many reviews are not replied by admin
* Suggestion for the non technical complaints (material): BISA AI should reply the comment which gives an opportunity to the user to explain further about of which materials are having wrong answers. Therefore, BISA AI can check the material and revise the "grey area" answers
* For predictive modelling, I choose multiclass classification for sentiment analysis: Negative (-1), Neutral (0), and Positive (1)
* I used four machine learning models for predictive modelling: Naive Bayes, Random Forest, Gradient Boosting Trees, and Support Vector Machine. Their hyperparameters have been tuned using Randomized Search. Also, they have been checked for overfitting or underfitting using 5-Fold Validation
* I focus on recall as the main evaluation metric from non positive classes (-1 or 0) such that machine can identify the negative or neutral reviews for faster giving solutions or maintenances
* Finally, after evaluating all of the models using their recall, it can be concluded that the best model has been achieved by Naive Bayes, which leads us to the chosen model to be deployed in the future. Also, I printed the confusion matrix to ensure about how many the true negatives and true neutrals are correctly predicted

Thank you for reading!
