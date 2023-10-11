# **News Popularity_Prediction in Multiple Social Media**
Machine Learning Resgression capston Project

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

## 1. Data Wrangling
---
After loading our datasets, we observed that in the news df, the source column contained 279 null values, so we replaced the null values with the source that has published the maximum number of news items. Further, we dropped the news items for which the published date was before Nov 2015 as this is trash data. We also performed the data cleaning by dropping duplicate rows and news items with null values in headlines. We treated the outliers in the dataset by using the 90th percentile method.

## 2. Standardization
---
We observed that the values of our dependent variables were quite large compared to the values in the independent variables. So to standardize the data we applied StandardScaler for data transformation.

## 3. EDA
---
In Exploratory Data Analysis, we categorized the sentimentTitle and sentimentHeadline into positive, neutral and negative sentiment categorical values. Then we observed that the number of sources publishing news items was quite large so to obtain a proper analysis we categorized the sources into 4 types, by grouping them on the number of news items published by each source. Further, we compared the popularity level of news items on the three social media platforms, observed the trend of popularity level based on sources and topics. We also observed the change in popularity level within the two days of publishing by using the time-span dataset.
 
## 4. Text Pre-processing
---
For handling the textual data in the news title and headline we used TF-IDF Vectorizer and CountVectorizer.

## 5. Encoding categorical values
---
We used one-hot encoding for converting the categorical columns such as source types, topics, sentiment category into numerical values so that our model can understand and extract valuable information from these columns.

## 6. Feature Selection
---
For feature selection, we used algorithms like ExtraTreeRegressor, which provides ordering features on the basis of their gini importance and helps in obtaining features which are more important compared to others for our model. Next we obtained correlation between the independent and dependent features to understand their relation.

## 7. Model Fitting
---
For modeling we tried the various regression algorithms like:
* Decision Tree
* Random Forest
* LightGBM
* Gradient Boosting
* KNN
* XGBoost

## 8. Hyper parameter Tuning
---
Tuning of hyperparameters is necessary for modeling to obtain better accuracy and to avoid overfitting. In our project, we used HalvingRandomizedSearchCV because 
* The Project deals with the large data
* High computation Time

## 9. Metrics Evaluation
---
We have used some of the metrics valuation techniques like MSE, RMSE, R2 Score, Adjusted R2, to obtain the accuracy and error rate of our models before and after hyperparameter tuning.

## 10. Feature Importance - SHAP Implementation
---
We implemented the SHAP value plot to obtain the importance of independent features in the model prediction to show the positive or negative relationship for each variable with the target.

## Conclusion
---

* **Sentiment Analysis**:
   - Negative sentiment dominated the news item titles, indicating a higher prevalence of negative-toned content.
   - Positive sentiment was the second most common, while neutral sentiment was the least prevalent.
   - Sentiment trends varied across different social media platforms, with Facebook users showing a preference for neutral sentiment content, LinkedIn users engaging more with negative sentiment, and GooglePlus users responding well to both positive and neutral sentiment.

* **Source Type Analysis**:
   - Source Type "A" was the primary contributor of news content, followed by Source Type "D." Source Type "B" published the fewest news items.
   - Popularity of news items varied by source type and social media platform, with some sources consistently producing engaging content.

* **Topic Popularity**:
   - Topics like "Economy" and "Microsoft" were more popular on Facebook and LinkedIn, indicating a preference for professional and tech-related discussions.
   - "Obama" and "Palestine" generated more interest on Facebook and LinkedIn, respectively.
   - Popularity trends for topics generally showed an increasing pattern across all three platforms over a two-day period.

* **Publication Trends**:
   - The dataset exhibited recurring patterns in news publication, with approximately seven-day cycles of higher and lower publication rates.
   - Specific hours during the day impacted the visibility of news items, suggesting the importance of timing for social media engagement.
     
* The Adjusted R2 Score obtained for all models revolved around 85% to 92% for all the three dependent variables.

* The accuracy obtained by the best model is 91%. From here we can also conclude that the TS columns in the time-span dataset have a higher influence on our dependent variables.

