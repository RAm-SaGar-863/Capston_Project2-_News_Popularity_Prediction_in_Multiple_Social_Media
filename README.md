# News Popularity Prediction in Multiple Social Media
![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

![Project Theme photo](https://github.com/RAm-SaGar-863/Capston_Project2-_News_Popularity_Prediction_in_Multiple_Social_Media/assets/128234583/942fd769-344b-48f9-9088-510f0676eca2)






![-----------------------------------------------------](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

## Table of Content
  * [Abstract](#abstract)
  * [Problem Statement](#problem-statement)
  * [Data Description](#data-description)
  * [Project Outline](#project-outline)
    - 1 [Data Wrangling](#data-wrangling)
    - 2 [Standardization](#standardization)
    - 3 [EDA](#eda)
    - 4 [Text Pre-processing](#text-pre-processing)
    - 5 [Encoding categorical values](#encoding-categorical-values)
    - 6 [Feature Selection](#feature-selection)
    - 7 [Model Fitting](#model-fitting)
    - 8 [Hyper-parameter Tuning](#hyper-parameter-tuning)
    - 9 [Metrics Evaluation](#metrics-evaluation)
    - 10 [Feature Importance - SHAP Implementation](#feature-importance-shap-implementation)
  * [Conclusion](#run)
  * [Reference](#reference)

---


# Abstract
News popularity on various social media platforms depends on multiple features like the topic, source of publication, time-span and sentiment score. Here we are provided with a dataset that contains news items and their respective social feedback on different platforms: Facebook, GooglePlus and LinkedIn.
Based on the previous trend, this data analysis and prediction with machine learning models can help us understand what are the reasons for news popularity on social media and obtain the best regression model.

# Problem Statement
A large data set of news items and their respective social feedback on multiple platforms: Facebook, Google+ and LinkedIn.The collected data relates to a period of 8 months, between November 2015 and July 2016, accounting for about 100,000 news items on four different topics: Economy, Microsoft, Obama and Palestine.

# Data Description
We have 13 dataset which are categorised into 2 types News_Final dataset and Time Span Dataset.
### **1. News_Final Dataset(1 Dataset)**: 
It contains information of news related to 4 topics Microsoft, Obama, Economy and Palestine collected from different sources and their popularity on 3 social media platform namely Facebook, GooglePlus and LinkedIn.

| Feature Name | Type | Description |
|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|IDLink| (numeric) | Unique identifier of news items|
|Title |(string)|Title of the news item according to the official media sources|
|Headline |(string)|Headline of the news item according to the official media sources|
|Source |(string)|Original news outlet that published the news item|
|Topic |(string)|Query topic used to obtain the items in the official media sources|
|PublishDate| (timestamp)|Date and time of the news items' publication|
|SentimentTitle| (numeric)|Sentiment score of the text in the news items' title|
|SentimentHeadline |(numeric)|Sentiment score of the text in the news items' headline|
|Facebook| (numeric)|Final value of the news items' popularity according to the social media source Facebook|
|GooglePlus| (numeric)|Final value of the news items' popularity according to the social media source Google+|
|LinkedIn |(numeric)|Final value of the news items' popularity according to the social media source LinkedIn|

### **2. Time Span Dataset(12 dataset)**:  
The 12 datasets are permutation of 4 topics and 3 platforms as stated above. Each dataset contains 2 days news popularity divided in 20 minutes interval after it is published i.e. 144 Time span features.

| Feature Name | Type | Description |
|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|IDLink |(numeric)| Unique identifier of news items|
|TS1 |(numeric)|Level of popularity in time slice 1 (0-20 minutes upon publication)|
|TS2 |(numeric)|Level of popularity in time slice 2 (20-40 minutes upon publication)|
|TS... |(numeric)|Level of popularity in time slice ...|
|...|...|...|
|...|...|...|
|TS144 |(numeric)|Final level of popularity after 2 days (2860-2880) upon publication|

---
# Project Outline

## 1. Data Wrangling
After loading our datasets, we observed that in the news df, the source column contained 279 null values, so we replaced the null values with the source that has published the maximum number of news items. Further, we dropped the news items for which the published date was before Nov 2015 as this is trash data. We also performed the data cleaning by dropping duplicate rows and news items with null values in headlines. We treated the outliers in the dataset by using the 90th percentile method.

## 2. Standardization
We observed that the values of our dependent variables were quite large compared to the values in the independent variables. So to standardize the data we applied StandardScaler for data transformation.
| Data Before Standardization  | Data After Standardization |
|--------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![image](https://user-images.githubusercontent.com/43884418/134707732-b0121b71-803c-4e91-be55-e89da3407267.png)|![image](https://user-images.githubusercontent.com/43884418/134707850-c0854391-76c6-48ae-8bf2-51b96ba5ae09.png) |

## 3. EDA
In Exploratory Data Analysis, we categorized the sentimentTitle and sentimentHeadline into positive, neutral and negative sentiment categorical values. Then we observed that the number of sources publishing news items was quite large so to obtain a proper analysis we categorized the sources into 4 types, by grouping them on the number of news items published by each source. Further, we compared the popularity level of news items on the three social media platforms, observed the trend of popularity level based on sources and topics. We also observed the change in popularity level within the two days of publishing by using the time-span dataset.

## 4. Text Pre-processing
For handling the textual data in the news title and headline we used TF-IDF Vectorizer and CountVectorizer.

## 5. Encoding categorical values
We used one-hot encoding for converting the categorical columns such as source types, topics, sentiment category into numerical values so that our model can understand and extract valuable information from these columns.

## 6. Feature Selection
For feature selection, we used algorithms like ExtraTreeRegressor, which provides ordering features on the basis of their gini importance and helps in obtaining features  which are more important compared to others for our model.
Next we obtained correlation between the independent and dependent features to understand their relation.

![image](https://user-images.githubusercontent.com/43884418/134711702-d95ada21-a7ed-4314-a340-8c7118edaf23.png)

## 7. Model Fitting
For modeling we tried the various regression algorithms like:
* Decision Tree Regression
* CatBoost
* LightGBM
* GradientBoosting 
* KNN

## 8. Hyper parameter Tuning
Tuning of hyperparameters is necessary for modeling to obtain better accuracy and to avoid overfitting. In our project, we used the
 - GridSearchCV, 
 - RandomizedSearchCV and 
 - HalvingRandomizedSearchCV.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
 We used plotly to showcase the parameter score of hyperparameters in different algorithms when doing hyperparameter tuning. In the plot below we are showing hyperparameter tuning of CatBoost using HalvingRandomizedSearchCV
![image](https://user-images.githubusercontent.com/35359451/134615300-a0d2a597-4195-4691-bf04-9eff13a2d58c.png)

## 9. Metrics Evaluation
We used some of the metrics valuation techniques like **MSE, RMSE, R2 Score, Adjusted R2, RMLSE**, to obtain the accuracy and error rate of our models before and after hyperparameter tuning.

## 10. Feature Importance - SHAP Implementation
We implemented the SHAP value plot to obtain the importance of independent features in the model prediction to show the positive or negative relationship for each variable with the target.

| Force Plot  | Summary Plot | Summary Plot (Bar Type) |
|----|----|----|
|![image](https://user-images.githubusercontent.com/35359451/134615402-ed7a3c28-c192-47e5-85b8-f356b223477d.png)|![image](https://user-images.githubusercontent.com/35359451/134615469-f41fde4e-f2a6-4f6b-8da2-307cd5379337.png)|![image](https://user-images.githubusercontent.com/35359451/134615492-d517fe35-766e-4099-b3e6-50227061d9ab.png)|
---
# Conclusion
 - Starting from loading the datasets, we covered data wrangling, EDA, feature selection and modeling.
 - The R2 Score obtained for all models revolved around **85% to 92%** for all the three dependent variables.
 - Further, we carried out hyperparameter tuning and obtained the best score and best parameters for all the models and there was not much improvement in the R2   Score.
 - So the accuracy obtained by the best model is **92%**. From here we can also conclude that the TS columns in the time-span dataset have a higher influence on our dependent variables.

 - **Content Optimization:** News organizations can leverage this Project to tailor their content creation strategies. By understanding the prevailing sentiment preferences and popular topics on each social media platform, they can optimize headlines and titles to resonate with the audience, thereby increasing the likelihood of user engagement.
 -  **Virality Prediction:** News organizations can predict the virality of news items by analyzing the source types and content attributes that lead to increased popularity. This knowledge enables content creators to prioritize and focus on creating content that has a higher likelihood of becoming viral, thereby reaching a wider audience.
 -  **Refining Ad Targeting Strategies:** Understanding the sentiments and preferences of users on GooglePlus provides valuable information for refining ad targeting strategies. Companies can use these insights to optimize the placement of advertisements based on the emotional context and preferences of the platform's users.
 -  **Optimized Timing Strategies:** The analysis of publication timing and visibility can guide content creators in determining the optimal times to publish news items on different social media platforms. By aligning publication times with platform-specific trends and audience activity patterns, organizations can enhance the visibility and reach of their content.
 -  **Optimizing Content Creators' Strategies:** Share insights from this project with news content creators to improve content listings, marketing, and overall approach. This collaboration boosts the success of news content creators on the platform, benefiting both creators and social media companies.
 - **Algorithmic Improvements for Search:** The project's machine learning models, especially those showing feature importance, can guide improvements in News Organizations search algorithms. By understanding the factors that contribute significantly to the popularity of news articles, News Orgnizations can refine its algorithms to deliver more relevant and engaging content in search results.
 - **Social Media Platform Development:**  If Social Media companies continues to invest in or develop social media platforms, the insights from this project can guide the design and features of these platforms. Understanding what drives engagement and popularity on other social media platforms can inform the development of features for their own social platforms.
 - **Optimizing Content Creators' Strategies:** Share insights from this project with news content creators to improve content listings, marketing, and overall approach. This collaboration boosts the success of news content creators on the platform, benefiting both creators and social media companies.
 




---
Here is a glimpse of few graphs we plotted, there are many more in the notebook please have a look.


