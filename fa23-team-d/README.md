# Project

## Description

### What is 311?
The purpose of the citizen hotline 311 is to report non-emergency issues and request information about your neighborhood. A knowledgeable agent will help you submit complaints or inquiries to the relevant municipal services when you dial 311. This frees up emergency numbers, such as 911, for dire circumstances. For example, you can use this service to report problems like broken road signs, abandoned cars, noise complaints, traffic light malfunctions, and road repairs.

You can report a wide variety of problems to 311, such as broken traffic signals, leaky hydrants, debris blocking roads, sidewalk repairs, and more. By using 311, you help ensure that non-emergency situations are managed effectively and free up emergency services to attend to critical life-or-death situations. Depending on where you live, you can usually use a mobile app specific to your city, like MyLA311 or NYC311, or you can call 311 to access this service. It's a great tool for answering questions from the public and making sure that non-urgent problems are resolved quickly without clogging up emergency lines.


## Purpose
The purpose of this project is to create a historical database for the City of Boston's 311 program. Through the project's analysis, any systemic flaws could be found and areas in need of improvement could be highlighted.

# Workflow

## Step 1:  Data Collection
<a href='https://data.boston.gov/dataset/311-service-requests'>311 Service Requests Dataset</a> - Dataset containing recorded requests from 2011 to 2023. ( the dataset is being updated every day)

<a href='https://data.boston.gov/dataset/311-service-requests/resource/b237f352-49d1-4423-804f-b478e4f24e61'>311 Service Requests Dataset Dictionary</a> - Dictionary for the dataset that explains the columns and their meanings, additionally providing some values from the column.

We downloaded all the datasets for each year and merged it to run an appropriate analysis on the whole dataset, rather than going year-by-year.

## Step 2:  Data Cleaning

The dataset provided is pretty decent, however, it has its own flaws. 

Some columns had no importance within the analysis, hence were dropped.

Some columns had a lot of missing values. Our team's goal was to save as much information as possible, so we filled some columns ourselves.

For example, zip-code columns, we run a reverse geocding algorithm using <a href='https://developers.google.com/maps/documentation/geocoding'>Google's Geocoding API</a>

Missing values in the on_time column could be filled by looking through closure dates and sla_target_dt ( targe dates ), however, that was inconsistent since the sla_target_dt had a lot of missing values.

For null values within the neighborhood column we combined them into a category of "No Neighborhood". (Two N/A values in the columns [nan, " " - string space charecter])

However, a lot questions that could be asked could be answered with other columns, which had nearly no null values at all.

## Step 3:  Base Questions

1) What is the total volume of requests per year, or how many 311 requests is the city receiving per year?
   
2) Which service requests are most common for the city overall AND by  NEIGHBORHOOD and how is this changing year over year by SUBJECT (department), REASON,QUEUE?
   
3) How is the case volume changing by submission channel SOURCE?
   
4) What is the average # of daily contacts by year?
   
5) Volume of top 5 request types (TYPE)  
   
6) Average goal resolution time by QUEUE 
   
7) Average goal resolution time by QUEUE and neighborhood
   
8) What % of service requests are closed (CLOSED_DT or CASE_STATUS) vs. no data (CASE_STATUS = null) vs. unresolved (CASE_STATUS = open)?

## Step 5:  Extension Work

### Extension 1

#### Description

Which requests are most common for census tracts defined as high social vulnerability based on the city’s social vulnerability index (note: this will take more data work because this is a geographic boundary area)

What patterns/ differences do you see between the 311 requests and service by high vulnerability groups vs. the rest of Boston?

#### Workflow

#### Results

### Extension 2

# Navigating Notebooks 
## Early analysis: 
1) [Notebook 1](notebooks/first_notebooks/analysis.ipynb)
2) [Notebook 2](notebooks/first_notebooks/prelimenary_analysis.ipynb)

## Answers to base questions:
1) [Notebook](notebooks/base-questions.ipynb)

## Extension Work: 

### Extension 1:
1) [Notebook (Neighborhood Predictor)](notebooks/models/neighborhood_predicter/model.ipynb)
2) [Notebook (Resolution Time Group Predicter)](notebooks/models/resolution_time_group_predicter/model.ipynb)
3) [Notebook (Final Results)](nodebooks/final_notebooks/poster_notebook.ipynb)

### Extension 2: 
1) [Notebook]()