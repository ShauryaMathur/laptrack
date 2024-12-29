# LAPTRACK
A major project for the course work at SUNY Buffalo, CSE 587 Data Intensive Computing(Fall 2024) under the guidance of Professor Chen Xu.

## Overview
In this project we have tried to build a web app where a user can search for laptops across multiple stores for comparing prices in one place and can get recommendations for similar laptops. In order to do so the project was executed in 3 phases as follows:
- **Phase 1: Data Collection and Analysis**
	 > Here the data was collected by scraping the public websites, namely: amazon.com, flipkart.com and bestbuy.com.
	 
	 > In order to scrape the data **BeautifulSoup** and **Selenium** was used to get the data and is stored in **sqlite database**.

	> The final data has over **4000 products** across the different stores and was analyzed to uncover hidden trends and patterns
- **Phase 2: Model Building**
	> In this part multiple ML models were built based on hypothesis built from Phase 1 data analysis.
	
	> ML models were built to analyze and validate hypothesis and uncover the patterns in the data.
	
	>  A total of **12 Regression models** were built and the **best 3 models** were selected for **hyperparameter tuning**. 

- **Phase 3: Deployment and Web App**
	> In this part a web app is built using **flask** as backend and **ReactJS** as the front end. For the **ETL pipeline**, using the **pySpark framework** the data is stored in **PostgreSQL**.
	
	> A **recommendation system** is built using  **cosine similarity** along with a **price predictor** using **ML models**. The predictor is presented as an **price estimator** for a given specs of a laptop.

## Setup and Executing Project
<br/>
<b>Step 1.</b> Download Docker Desktop.
<br/>

> The link contains the steps to install docker on mac, linux and Windows.

<br/>
<b>Step 2.</b> Start Docker Desktop and in the docker terminal and run the following command 
<pre>
docker-compose up --build
</pre> 
<br/>
<b>Step 3.</b> It should now directly open up the local hosted application at port 3000. In case it doesn't open up, go to your browser and put the following in the URL bar
<pre>
localhost:3000/
</pre>
<br/>
<b>Step 4.</b> You can use the following sample login credentials to explore the app:
<pre>
user@example.com
user123
</pre>

## Highlights 

<br/>
<b>1.</b> Created ETL Pipeline
<br/>

> An ETL pipeline is written in Python.

> The pipeline periodically scrapes laptop data (weekly CRON jobs are set) from Amazon, Bestbuy, and Flipkart using BeautifulSoup, Selenium, and requests modules in Python and creates CSV files for the scraped data.

> The CSV files are read using pandas, cleaned (uncleaned and unstructured data is normalized), and then combined into a master data CSV file.

> The combined data is preprocessed again and dumped to a PostgreSQL using PySpark.

<br/>
<b>2.</b> Developed the backend and front end of the web app.
<br/>

>The backend for the application is developed using Flask(Python with SQLAlchemy).

>The applications has various endpoints for CRUD operations and to expose the recommendation engine and ML models for the UI.

>PostgreSQL Database is used along with PySpark.

>Front-end is developed using ReactJS.

>The entire application is Dockerised for portability and ease of setup.

<b>3.</b> Implemented a content-based recommendation system
<br/>

>A content-based recommendation system was implemented using TfidfVectorizer and cosine similarity using the sklearn library.

>The recommendation engine recommends similar laptops to users based on similar laptop specifications.

<b>4.</b> Trained and deployed ML models for price predictions
<br/>
>Multiple ML models were trained and tested on the clean data to accurately predict price of laptops based on laptop specifications.

>XGBoost and GBDT were among the top performers and hence were pickled along with required scalers and encoders.

>The application reads admin user input and feeds it to the trained models and predicts the price based off the specifications of the laptop.

>There is a page in the admin panel that lets the admin analyze price variations across laptop brands with given specifications.

## Project Demo Video
[Video Demo YT](https://youtu.be/WnHhlB1WFgM)

