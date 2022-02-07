# IBM Applied Data Science Capstone Project

The PowerPoint slides for this project can be found at <a href="https://github.com/ZhengEnThan/IBM-Applied-Data-Science-Capstone-Project/blob/main/Capstone_Presentation.pptx" target="_blank">Capstone_Presentation.pptx</a>.

## Executive summary
In this capstone project, we will predict if the SpaceX Falcon 9 first stage will land successfully using several machine learning classification algorithms.
The main steps in this project include:

- Data collection, wrangling, and formatting
- Exploratory data analysis
- Interactive data visualization
- Machine learning prediction

Our graphs show that some features of the rocket launches have a correlation with the outcome of the launches, i.e., success or failure. It is also concluded that decision tree may be the best machine learning algorithm to predict if the Falcon 9 first stage will land successfully.

## Introduction
In this capstone, we will predict if the Falcon 9 first stage will land successfully. SpaceX advertises Falcon 9 rocket launches on its website with a cost of 62 million dollars; other providers cost upward of 165 million dollars each, much of the savings is because SpaceX can reuse the first stage. Therefore if we can determine if the first stage will land, we can determine the cost of a launch. This information can be used if an alternate company wants to bid against SpaceX for a rocket launch.

Most unsuccessful landings are planned. Sometimes, SpaceX will perform a controlled landing in the ocean. The main question that we are trying to answer is, for a given set of features about a Falcon 9 rocket launch which include its payload mass, orbit type, launch site, and so on, will the first stage of the rocket land successfully?

## Methodology
The overall methodology includes:
1. Data collection, wrangling, and formatting, using:
  - SpaceX API
  - Web scraping
2. Exploratory data analysis (EDA), using:
  - Pandas and NumPy 
  - SQL
3. Data visualization, using:
  - Matplotlib and Seaborn
  - Folium
  - Dash
4. Machine learning prediction, using
  - Logistic regression
  - Support vector machine (SVM)
  - Decision tree
  - K-nearest neighbors (KNN)

## Data collection using SpaceX API
<a href="https://github.com/ZhengEnThan/IBM-Applied-Data-Science-Capstone/blob/main/1_Data%20Collection%20API.ipynb" target="_blank">1_Data Collection API.ipynb</a>

Libraries or modules used: requests, pandas, numpy, datetime

- The API used is <a href="https://api.spacexdata.com/v4/rockets/" target="_blank">here</a>.
- The API provides data about many types of rocket launches done by SpaceX, the data is therefore filtered to include only Falcon 9 launches.
- The API is accessed using requests.get().
- The json result is converted to a dataframe using the json_normalize() function from pandas.
- Every missing value in the data is replaced the mean the column that the missing value belongs to. 
- We end up with 90 rows or instances and 17 columns or features. 

## Data Collection with Web Scraping
<a href="https://github.com/ZhengEnThan/IBM-Applied-Data-Science-Capstone/blob/main/2_Data%20Collection%20with%20Web%20Scraping.ipynb" target="_blank">2_Data Collection with Web Scraping.ipynb</a>

Libraries or modules used: sys, requests, BeautifulSoup from bs4, re, unicodedata, pandas

- The data is scraped from  <a href="https://en.wikipedia.org/w/index.php?title=List_of_Falcon_9_and_Falcon_Heavy_launches&oldid=1027686922" target="_blank">List of Falcon 9 and Falcon Heavy launches</a>.
- The website contains only the data about Falcon 9 launches.
- First, the Falcon9 Launch Wiki page is requested from the url and a BeautifulSoup object is created from response of requests.get().
- Next, all column/variable names are extracted from the HTML table header by using the find_all() function from BeautifulSoup.
- A dataframe is then created with the extracted column names and entries filled with launch records extracted from table rows.
- We end up with 121 rows or instances and 11 columns or features. 

## EDA with Pandas and Numpy
<a href="https://github.com/ZhengEnThan/IBM-Applied-Data-Science-Capstone/blob/main/3_EDA.ipynb" target="_blank">3_EDA.ipynb</a>

Libraries or modules used: pandas, numpy

Functions from the Pandas and NumPy libraries such as value_counts() are used to derive basic information about the data collected, which includes:
- The number of launches on each launch site
- The number of occurrence of each orbit
- The number and occurrence of each mission outcome

## EDA with SQL
<a href="https://github.com/ZhengEnThan/IBM-Applied-Data-Science-Capstone/blob/main/4_EDA%20with%20SQL.ipynb" target="_blank">4_EDA with SQL.ipynb</a>

Framework: IBM DB2
Libraries or modules used: ibm_db

The data is queried using SQL to answer several questions about the data such as:
- The names of the unique launch sites in the space mission
- The total payload mass carried by boosters launched by NASA (CRS)
- The average payload mass carried by booster version F9 v1.1
