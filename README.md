# Capston_Project2-_News_Popularity_Prediction_in_Multiple_Social_Media
Machine Learning Resgression Project

## Problem Statement
---
The project's goal is to analyze a dataset of 100,000 news articles and their social feedback on platforms like Facebook, Google+, and LinkedIn over an eight-month period from November 2015 to July 2016. The objective is to perform Exploratory Data Analysis (EDA) and build machine learning models to predict a news article's popularity on these platforms 48 hours after publication. The dataset includes articles on four topics: Economy, Microsoft, Obama, and Palestine. The project aims to provide insights and predictions that can help content creators and news organizations optimize their strategies.

## Project Summary 
---
This comprehensive data analysis and machine learning project embarked on an exploration of a substantial dataset encompassing a span of eight months from November 2015 to July 2016. Within this dataset, an extensive collection of news items was meticulously examined, with a focus on four distinct topics: Economy, Microsoft, Obama, and Palestine. These news items were distributed across three prominent social media platforms, namely Facebook, GooglePlus, and LinkedIn.we also have 12 social feedback dataset which contains the popularity level of news items in incremental time slices of 20 min after publication.

* As the first step of our experiment, we performed Data Cleaning by removing trash and duplicate data, applied null value treatment and removed outliers in the data set using the 90th percentile quantile method. We further applied the Standardization technique for feature scaling.

* In Exploratory Data Analysis, we categorized SentimentTitle, SentimentHeadline and sources to extract some meaningful insights from the data. Then we compared popularity between the social media platforms using multiple plots.


* Sentiment Analysis unearthed compelling patterns, revealing that negative sentiment overwhelmingly dominated news item headlines, closely followed by positive sentiment, while neutral sentiment proved to be the least prevalent. This discovery underscored the emotionally charged nature of news content, and intriguingly, it illuminated distinct user preferences for various sentiment types on each social media platform.

* Source Type Analysis shed light on the key contributors of news content within the dataset. "Source Type A" emerged as the primary source of news items, with "Source Type D" following closely behind, while "Source Type B" exhibited the lowest volume of published news items. These findings offered valuable insights into the varying popularity and engagement levels associated with different source types across platforms.

* Topic Analysis unraveled the diverse preferences of social media users, highlighting that topics such as "Economy" and "Microsoft" enjoyed heightened engagement on specific platforms, whereas "Palestine" and "Obama" exhibited nuanced popularity trends across different platforms.

* Popularity Trends across all three social media platforms demonstrated a consistent upward trajectory over the two-day observation period. Facebook consistently outperformed its counterparts, boasting the highest average popularity, while GooglePlus consistently lagged behind, indicating substantial discrepancies in audience engagement across platforms.

* Publication Timing and Visibility analyses underscored the critical role of timing in maximizing the reach and impact of news items on social media. Platform-specific trends and optimal publication times emerged as pivotal factors for achieving broader visibility.


* We applied text-preprocessing techniques to transform the headline and title of the news items.

* Feature Importance Analysis, powered by ExtraTreesRegressor, unveiled the significance of diverse features in predicting social media popularity. Factors such as source type, sentiment, topic, and publication timing were identified as crucial determinants of news item popularity.

* Machine Learning Models played a pivotal role in this project, with an array of models—including  Decision Tree Regressor, Random Forest Regressor, LightGBM Regressor, k-Nearest Neighbors (KNN) Regressor, and XGBoost Regressor being employed to predict news item popularity. The models' performance was assessed using the "Adjusted R^2" metric, with Random Forest Regressor and LightGBM Regressor emerging as standout performers in terms of predictive accuracy.

* SHAP (SHapley Additive exPlanations) Analysis served as a vital tool for interpreting machine learning model predictions and identifying the features that exerted the most significant influence on popularity forecasts.

In summary, this project has provided a comprehensive and nuanced understanding of the factors shaping the popularity of news items on diverse social media platforms. The insights and actionable recommendations derived from this analysis offer content creators, marketers, and social media strategists valuable tools for optimizing their strategies. By aligning their efforts with platform-specific preferences, leveraging predictive models, and staying attuned to the ever-evolving landscape of social media, organizations can enhance their content's impact and reach, thereby achieving their primary objective of maximizing engagement and audience reach in the digital realm.

## Input Files:
---
Facebook_Economy.csv\
Facebook_Microsoft.csv\
Facebook_Obama.csv\
Facebook_Palestine.csv\
GooglePlus_Economy.csv\
GooglePlus_Microsoft.csv\
GooglePlus_Obama.csv\
GooglePlus_Palestine.csv\
LinkedIn_Economy.csv\
LinkedIn_Microsoft.csv\
LinkedIn_Obama.csv\
LinkedIn_Palestine.csv\
News_Final.csv

## Variables Description:
---

* #### Variables  of News Dataset

  * **IDLink (numeric):** Unique identifier of news items
  * **Title (string):** Title of the news item according to the official media sources
  * **Headline (string):** Headline of the news item according to the official media sources
  * **Source (string):** Original news outlet that published the news item
  * **Topic (string):** Query topic used to obtain the items in the official media sources
  * **PublishDate (timestamp):** Date and time of the news items' publication
  * **SentimentTitle (numeric):** Sentiment score of the text in the news items' title
  * **SentimentHeadline (numeric):** Sentiment score of the text in the news items' headline
  * **Facebook (numeric):** Final value of the news items' popularity according to the social media source Facebook
  * **GooglePlus (numeric):** Final value of the news items' popularity according to the social media source Google+
  * **LinkedIn (numeric):** Final value of the news items' popularity according to the social media source LinkedIn


* #### Variables of Social Feedback Datasets

  * **IDLink (numeric):** Unique identifier of news items
  * **TS1 (numeric):** Level of popularity in time slice 1 (0-20 minutes upon publication)
  * **TS2 (numeric):** Level of popularity in time slice 2 (20-40 minutes upon publication)
  * **TS... (numeric):** Level of popularity in time slice ...
  * **TS144 (numeric):** Final level of popularity after 2 days upon publication

## The project follows a step-by-step process, as outlined below:---
---
