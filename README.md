# Web Page Classification

<img src="https://user-images.githubusercontent.com/84275757/178939224-5e9176d8-99f3-4cfe-9a3b-725a124e628f.png" width="300" height="300" />




## :small_blue_diamond: Project Overview

•	Utilized dataset which contained the features web page id, domain, URL, and 9 predefined tags (classes) required for predicting the class of the web page.

•	Performed Exploratory Data Analysis (EDA) for target exploration and extracted features using Bag of words, character-n-grams, TFIDF techniques.

•	Models were trained using logistic regression, naive bayes, decision trees, and random forest and evaluated using weighted F1 score. The logistic regression model gave highest weighted F1 score upto 0.7988 and outperformed other three models.

## :small_blue_diamond: Motivation/Purpose

•	The abundant amount of data available on the web makes it essential to develop efficient and robust models for web mining tasks. Web page classification is the process of assigning a web page to a particular predefined category based on labelled data. 

• Classification of Web page content is vital to many tasks in Web information retrieval such as maintaining Web directories and focused crawling which is used to selectively seek out web pages that are relevant to a pre-defined set of topics.

•	As an example, collecting and mining personal content on patients’ experiences with respect to disease symptoms and progression, treatment management, side effects and effectivenes can be very helpful in understanding a disease better.

•	The understanding attainable through mining this voluntarily contributed web content would be extremely expensive and time-consuming to capture via web queries. For example, a general query such as ‘breast cancer stories’ would pull up over 182 million results using Google web search.

•	However, if we can build an accurate classifier to pinpoint the right web pages that precisely contains patients' experiences using the URLs and page content, it can save a lot of time and compute for collecting this information.

## :small_blue_diamond: Dataset Overview

<img src="https://user-images.githubusercontent.com/84275757/178946648-b120a701-3e84-49e2-8111-14b1365818d3.png" width="800" height="300" />


In this case study, we are provided with URLs from 53000+ web pages. The dataset contains the following features:

• web page_ID: Unique ID for the web page (1,2,3.... )

• Domain: Domain of the web page (Example: www.fiercepharma.com)

• Url: Complete URL of the web page (Example: http://www.fiercepharma.com/marketing/tecfidera-gilenya-and-aubagio-s-3-way-battle-for-ms-share-about-to-get-more-interesting)

• Tag (Target): Tag (class) of the web page

The 9 predefined tags are:-

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



## :gear: Technologies Used
![Screenshot (151)](https://user-images.githubusercontent.com/84275757/173030213-f8e8a1d1-86d5-4782-abf1-928889fc6677.png)
<img alt="numpy" src="https://user-images.githubusercontent.com/84275757/173030594-fba1e76a-d6c5-4928-ac77-4057b1028025.png" width="200" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/173031448-9e3e22df-53a6-480d-8a24-56c3b269a70a.png" width="250" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/178946219-fab6a2cf-c6a3-4615-9b45-df5a66fb692d.png" width="300" height="150" />
<img src="https://user-images.githubusercontent.com/84275757/173031755-5d73c113-a4ca-4119-a693-885972be603b.png" width="350" height="150" />
<img src="https://user-images.githubusercontent.com/84275757/173031858-ebcd32fb-88d0-459a-8147-8fcec5b462d5.png" width="200" height="200" />
<img src="https://user-images.githubusercontent.com/84275757/173031918-1584d7ce-f852-4c47-a3bb-391fadff9a6d.png" width="300" height="200" />


## :small_blue_diamond: Methodology

:bulb: Note:- Please turn on Light theme in Github to see the below images properly (most captions and axes are not visible in dark theme).

<img src="https://user-images.githubusercontent.com/84275757/178946982-7dd06c90-7b1a-495b-b074-945f6238373b.png" width="700" height="800" />

## :small_blue_diamond: Exploratory Data Analysis (EDA)
Some snapshots from EDA 

### Target Exploration

<img src="https://user-images.githubusercontent.com/84275757/178948604-ffe41d68-91b2-4183-947d-67b2bd7d620a.png" width="700" height="400" />
Here we look at frequency distribution of each tag. There are 2 major categories apart from others i.e news and publication. Public profiles, forums and conferences lie in the next bracket and guidelines have the lowest frequency in the dataset.

### Understanding the common words used in the URLs: WordCloud

<img src="https://user-images.githubusercontent.com/84275757/178954644-98c44c6b-01b6-4979-9821-25567c364300.png" width="700" height="400" />

In this wordcloud, we can see the commonly occurring words in the dataset that are in ranking according to their sizes like biomedcentral articles is the biggest word, hence the most occurring one. Other words like org content, article https, find doctor also have good frequency in the dataset.

<img src="https://user-images.githubusercontent.com/84275757/178955442-1244f425-5309-4b42-a21a-d8f9f817e1ab.png" width="700" height="400" />

In this wordcloud for thesis tag, we can see the commonly occurring words in the dataset that are in ranking according to their sizes like edu, handle is the biggest word, hence the most occurring one. Other words like https, ecommons, library also have good frequency in the dataset. Similarly for all tags, wordclouds can be built to get a better visual understanding of the data.


## :small_blue_diamond: Data Preproccessing

Done after EDA, to see any hidden patterns in raw data and avoid any bias.

Here we simply have domain and URL and these are neither numeric nor categorical variable as each URL is unique. The URLs in the dataset can be considered as a single string since the words in the URL have no spaces. Instead, there are 2 types of separators here '/' and '-'. We can replace these by spaces and we can get individual words this way. 
Therefore tokenization of the words was done to do the necessary cleaning.

## :small_blue_diamond: Model Building

This is a multi-class classification problem. The train and test data split should done based on Domain-Tag combination, such that no 2 URLs for the same class and domain are kept in the train and test respectively because in that case domain can be directly mapped to the tag and that would be a leakage.

The 4 models were built using:
1. Logistic Regression
2. Naive Bayes
3. Decision Tree
4. Random Forest

## :small_blue_diamond: Evaluation metrics

Since this a multi-classification problem we will use weighted F1 score which basically assigns weights proportional to the class frequency in the train set.
Group K fold Cross Validation (5 Fold) has been also used to prevent overfitting. In group K-Fold, the same group will not appear in two different folds. The folds are approximately balanced in the sense that the number of distinct groups is approximately the same in each fold.

## :small_blue_diamond: Model Performance

The complete implementation of all models can be seen at [Web Page Classification notebook.](Web_Page_Classificaton.ipynb)

The Naive Bayes model gave best score upto 
Weighted F1 score= 0.7474

The Logistic Rehression model gave best score upto
Weighted F1 score= 0.7988

The Decision Tree model gave best score upto
Weighted F1 score= 0.6521

The Random Forest model gave best score upto
Weighted F1 score= 0.7319


<img src="https://user-images.githubusercontent.com/84275757/178959662-b0d8e5e9-265e-4571-9480-561a6f15ff05.png" width="700" height="300" />


With this visual depiction, we can clearly see that Logistic Regression is getting the best performance and interestingly Tree Based methods are performing badly. Though the scores are not very stable due to the large number of classes and few samples. With better data and amount of samples, score can be improved and we can use ensemble methods to get a better classifier model for web pages.



