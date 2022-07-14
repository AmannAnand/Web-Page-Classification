# Web Page Classification

<img src="https://user-images.githubusercontent.com/84275757/178939224-5e9176d8-99f3-4cfe-9a3b-725a124e628f.png" width="300" height="300" />




## :small_blue_diamond: Project Overview

•	Utilized dataset which contained many features of customer demographics, transaction data, and bank branch data required for predicting customer churn.

•	Performed extensive Exploratory Data Analysis (EDA) to select the best features.

•	Models were trained using logistic regression and evaluated using different evaluation metrics. The rfe_top_10 model gave score of 
AUC-ROC=0.8118, Recall=0.2253 and outperformed all three models.

## :small_blue_diamond: Motivation/Purpose

•	The abundant amount of data available on the web makes it essential to develop efficient and robust models for web mining tasks. Web page classification is the process of assigning a web page to a particular predefined category based on labelled data. 

• Classification of Web page content is vital to many tasks in Web information retrieval such as maintaining Web directories and focused crawling which is used to selectively seek out web pages that are relevant to a pre-defined set of topics.

•	As an example, collecting and mining personal content on patients’ experiences with respect to disease symptoms and progression, treatment management, side effects and effectivenes can be very helpful in understanding a disease better.

•	The understanding attainable through mining this voluntarily contributed web content would be extremely expensive and time-consuming to capture via web queries. For example, a general query such as ‘breast cancer stories’ would pull up over 182 million results using Google web search.

•	However, if we can build an accurate classifier to pinpoint the right web pages that precisely contains patients' experiences using the URLs and page content, it can save a lot of time and compute for collecting this information.

## :small_blue_diamond: Dataset Overview

In this case study, we are provided with URLs from 53000+ web pages. The dataset contains the following features:

• web page_ID: Unique ID for the web page (1,2,3.... )

• Domain: Domain of the web page (Example: www.fiercepharma.com)

• Url: Complete URL of the web page (Example: http://www.fiercepharma.com/marketing/tecfidera-gilenya-and-aubagio-s-3-way-battle-for-ms-share-about-to-get-more-interesting)

• Tag (Target): Tag (class) of the web page

Basically given the complete url, predict the tag a web page belongs to out of 9 predefined tags as given below:

1. People profile
2. Conferences/Congress
3. Forums
4. News article
5. Clinical trials
6. Publication
7. Thesis
8. Guidelines
9. Others


## :small_blue_diamond: Problem Statement

The objective is to build a classifier that can classify the web pages into their respective classes (Each web page can belong to only 1 class).

## :small_blue_diamond: Hypothesis Generation
Some of the hypotheses are listed below:

### Demographics
•	Are females less likely to churn than males?

•	Are young customers more likely to churn?

•	Are customers located in Tier-1 cities more likely to churn?

•	Are married people less likely to churn?

•	Are older customers less likely to churn?

•	Are customers in the lower income bracket more likely to churn?

•	Are customers in the middle income bracket more likely to churn?

•	Are customers in the higher income bracket more likely to churn?

### Behaviour
•	Are vintage customers less likely to churn?

•	Are customers with higher average balance less likely to churn?

•	Are customers dropping monthly balance high likely to churn?

### Psychographic
•	Do customers that are inherently more loyal less likely to churn?

•	Do customers that have interest in sports more likely to churn?

•	Do customers who go to movies often are highly likely to churn?

### Other factors
•	Customers getting a low rate of interest in fixed deposit compared to competitor banks are more likely to churn?

•	Customers getting a low rate of interest in recurring deposit compared to competitor banks are more likely to churn?

•	Customers incurring a high rate of interest in house loans compared to competitor banks are more likely to churn?


## :gear: Technologies Used
![Screenshot (151)](https://user-images.githubusercontent.com/84275757/173030213-f8e8a1d1-86d5-4782-abf1-928889fc6677.png)
<img alt="numpy" src="https://user-images.githubusercontent.com/84275757/173030594-fba1e76a-d6c5-4928-ac77-4057b1028025.png" width="200" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/173031448-9e3e22df-53a6-480d-8a24-56c3b269a70a.png" width="250" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/173031755-5d73c113-a4ca-4119-a693-885972be603b.png" width="350" height="150" />
<img src="https://user-images.githubusercontent.com/84275757/173031858-ebcd32fb-88d0-459a-8147-8fcec5b462d5.png" width="200" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/173031918-1584d7ce-f852-4c47-a3bb-391fadff9a6d.png" width="300" height="200" />


## :small_blue_diamond: Methodology

:bulb: Note:- Please turn on Light theme in Github to see the below images properly (most captions and axes are not visible in dark theme).

<img src="https://user-images.githubusercontent.com/84275757/173101975-d54eb319-941e-46b4-9fe2-97f6c2a267b0.png" width="500" height="700" />

## :small_blue_diamond: Exploratory Data Analysis (EDA)
Some snapshots from EDA 
### Univariate Analysis

<img src="https://user-images.githubusercontent.com/84275757/173103836-eba4293a-7896-462f-aab2-586866534852.png" width="1000" height="300" />
<img src="https://user-images.githubusercontent.com/84275757/173103990-251cfdba-89d7-45ef-a07a-447e99425ea2.png" width="600" height="400" />

### Bivariate Analysis

<img src="https://user-images.githubusercontent.com/84275757/173104066-ca35dea8-7a66-4d96-ab52-dcc2373b0497.png" width="1000" height="300" />
<img src="https://user-images.githubusercontent.com/84275757/173104117-b84bfce8-c85f-4d26-abd3-21c7bf2e086b.png" width="600" height="400" />

### Multivariate Analysis

<img src="https://user-images.githubusercontent.com/84275757/173104598-4b09f363-39b6-4b28-9c6c-3f73eb6bf16f.png" width="700" height="400" />
<img src="https://user-images.githubusercontent.com/84275757/173104277-357b86c0-d23e-4128-95c2-4be34870b8b2.png" width="600" height="400" />

Complete EDA in detail can be seen in [EDA Notebook.](Customer_Churn_Prediction_EDA.ipynb)

## :small_blue_diamond: Conclusions from EDA
•	For debit values, we see that there is a significant difference in the distribution for churn and non churn and it might be turn out to be an important feature

•	For all the balance features the lower values have much higher proportion of churning customers

•	For most frequent vintage values, the churning customers are slightly higher, while for higher values of vintage, we have mostly non churning customers which is in sync with the age variable

•	We see significant difference for different occupations and certainly would be interesting to use as a feature for prediction of churn.


## :small_blue_diamond: Data Preproccessing

Done after EDA, to see any hidden patterns in raw data and avoid any bias.
### Missing values
Gender: It had some missing values but since there was a good mix of males and females and arguably missing values cannot be filled with any one of them. A seperate category was created by assigning the value -1 for all missing values in this column.

Dependents, occupation and city: The missing values in these columns were filled with mode of respective columns.

Days since Last Transaction: A fair assumption was made on this column as this is number of days since last transaction in 1 year, we can substitute missing values with a value greater than 1 year say 999.

### Preprocessing
There were a lot of outliers in the dataset especially when it comes to previous and current balance features. Also, the distributions are skewed for these features, so two steps were taken to deal with that here:

1. Log Transformation

2. 	Standard Scaler
 
## :small_blue_diamond: Model Building

Three separate models were built and trained using logistic regression.
1.	Model with all features 
2.	Model with baseline features
3.	Model with top 10 features obtained from reverse feature elimination (RFE)

## :small_blue_diamond: Evaluation metrics

Since this is a binary classification problem, we could use the following 2 popular metrics:
1.	Recall
2.	Area under the Receiver operating characteristic curve (AUC-ROC)

Now, we are looking at the recall value here because a customer falsely marked as churn would not be as bad as a customer who was not detected as a churning customer and appropriate measures were not taken by the bank to stop him/her from churning

The ROC AUC is the area under the curve when plotting the (normalized) true positive rate (x-axis) and the false positive rate (y-axis).
Our main metric here would be Recall values, while AUC ROC Score would take care of how well predicted probabilites are able to differentiate between the 2 classes.

Cross Validation (5 Fold) has been also used to prevent overfitting.

## :small_blue_diamond: Model Performance

The complete implementation of all models using logistic regression can be seen at [Customer Churn Prediction using Logistic Regression notebook.](Customer_Churn_Prediction_Logistic_Regression.ipynb)

The all features model gave best score of 
AUC-ROC=0.8058, Recall=0.2405

The baseline model gave best score of
AUC-ROC=0.7822, Recall=0.1236

The rfe_top_10 model gave best score of 
AUC-ROC=0.8118, Recall=0.2253

<img src="https://user-images.githubusercontent.com/84275757/173106395-4657cc7f-2da3-4055-b2aa-a760882e60a5.png" width="500" height="300" />


Thus, rfe_top_10 model performed the best among all the three models.



