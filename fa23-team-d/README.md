## Table of Contents
<ol>
    <li style='font-size:32px'>
        <a href='#project' >Project</a>
        <ol style='font-size:20px;'>
            <li><a href='#description'>Description</a></li>
            <li><a href='#purpose'>Purpose</a></li>
        </ol>
    </li>
    <li style='font-size:32px'>
        <a href=''>Workflow</a>
        <ol style='font-size:20px;'>
            <li><a href='#step-1-data-collection'>Data Collection</a></li>
            <li><a href='#step-2-data-cleaning'>Data Cleaning</a></li>
            <li><a href='#step-3-base-questions'>Base Questions</a></li>
            <li><a href='#step-4-extension-work'>Extension Work</a></li>
        </ol>
    </li>
    <li style='font-size:32px'>
        <a href='#navigating-notebooks'>Navigating Notebooks</a>
        <ol style='font-size:20px;'>
            <li><a href='#early-analysis'>Early Analysis<a></li>
            <li><a href='#answers-to-base-questions'>Answers to base questions</a></li>
            <li><a href='#extension-work'>Extension Work</a></li>
        </ol>
    </li>
</ol>
    

# Project
## Description

### What is 311?
The purpose of the citizen hotline 311 is to report non-emergency issues and request information about your neighborhood. A knowledgeable agent will help you submit complaints or inquiries to the relevant municipal services when you dial 311. This frees up emergency numbers, such as 911, for dire circumstances. For example, you can use this service to report problems like broken road signs, abandoned cars, noise complaints, traffic light malfunctions, and road repairs.

You can report a wide variety of problems to 311, such as broken traffic signals, leaky hydrants, debris blocking roads, sidewalk repairs, and more. By using 311, you help ensure that non-emergency situations are managed effectively and free up emergency services to attend to critical life-or-death situations. Depending on where you live, you can usually use a mobile app specific to your city, like MyLA311 or NYC311, or you can call 311 to access this service. It's a great tool for answering questions from the public and making sure that non-urgent problems are resolved quickly without clogging up emergency lines.


## Purpose
The purpose of this project is to create a historical database for the City of Boston's 311 program. Through the project's analysis, any systemic flaws could be found and areas in need of improvement could be highlighted.

# Workflow

## Step 1: Data Collection
<a href='https://data.boston.gov/dataset/311-service-requests'>311 Service Requests Dataset</a> - Dataset containing recorded requests from 2011 to 2023. ( the dataset is being updated every day)

<a href='https://data.boston.gov/dataset/311-service-requests/resource/b237f352-49d1-4423-804f-b478e4f24e61'>311 Service Requests Dataset Dictionary</a> - Dictionary for the dataset that explains the columns and their meanings, additionally providing some values from the column.

We downloaded all the datasets for each year and merged it to run an appropriate analysis on the whole dataset, rather than going year-by-year.

<a href='https://data.boston.gov/dataset/climate-ready-boston-social-vulnerability'>Climate Ready Boston Social Vulnerability</a>


## Step 2: Data Cleaning

The dataset provided is pretty decent, however, it has its own flaws. 

Some columns had no importance within the analysis, hence were dropped.

Some columns had a lot of missing values. Our team's goal was to save as much information as possible, so we filled some columns ourselves.

For example, zip-code columns, we run a reverse geocding algorithm using <a href='https://developers.google.com/maps/documentation/geocoding'>Google's Geocoding API</a>

Missing values in the on_time column could be filled by looking through closure dates and sla_target_dt ( targe dates ), however, that was inconsistent since the sla_target_dt had a lot of missing values.

For null values within the neighborhood column we combined them into a category of "No Neighborhood". (Two N/A values in the columns [nan, " " - string space charecter])

However, a lot questions that could be asked could be answered with other columns, which had nearly no null values at all.

## Step 3: Base Questions

1) What is the total volume of requests per year, or how many 311 requests is the city receiving per year?
   
2) Which service requests are most common for the city overall AND by  NEIGHBORHOOD and how is this changing year over year by SUBJECT (department), REASON,QUEUE?
   
3) How is the case volume changing by submission channel SOURCE?
   
4) What is the average # of daily contacts by year?
   
5) Volume of top 5 request types (TYPE)  
   
6) Average goal resolution time by QUEUE 
   
7) Average goal resolution time by QUEUE and neighborhood
   
8) What % of service requests are closed (CLOSED_DT or CASE_STATUS) vs. no data (CASE_STATUS = null) vs. unresolved (CASE_STATUS = open)?

## Step 4: Extension Work

### Extension 1

#### Description

Which requests are most common for census tracts defined as high social vulnerability based on the city’s social vulnerability index (note: this will take more data work because this is a geographic boundary area)

What patterns/ differences do you see between the 311 requests and service by high vulnerability groups vs. the rest of Boston?

#### Workflow

Our first approach was to experiment with some Machine Learning models and see if it can pick up anything.

We used the Social Vulnerability Index dataset and merged it with the original dataset. 

The strategy for merging can be seen in the notebooks for the models.

One of the models we decided to work with is to create a resolution_time_group_predicter.

We split all the resolution times into 5 groups: daily, weekly, monthly, yearly and > yearly. Each group is the amount of time need for a task to be finished.

We wanted to see whether there is a criteria that could be impactfull on the classification. However, the feature importance showed that the Social Vulnerability Index dataset had no importance.

Therefore, we decided to manually go over the dataset. We revised our merging strategy, fixed some neighborhood incosistencies. Normalized SV entries using 3 different approaches.

(MAHDI, 1 PARAGRAPH DESCRIBING YOUR WORK)

### Extension 2

#### Description

The second extension analyzed rates of closure for the same types of requests by neighborhoods, city council districts, neighborhood services districts, and zip codes.

#### Workflow

We focused on reason to group similar types of requests. However, we found that there were 54 unique values in request. In order to group further, we created a column called reason_grouped to make our graphs more readable. In order to create each graph, we grouped the category of area and reason_grouped, to provide our x-axis and key, respectively, and found the mean of the resolution time in days, which became our y-axis. As a result, we were able to see for each neighborhood, district, etc. which groups of reasons had higher request times as well as the overall distribution of reason grouped across the distinct neighborhoods, districts, etc. 

#### Results
We found that Urban Safety and Maintenance had the highest average resolution time when compared to each reason_grouped across all categories and its distribution varied, meaning that some of the average resolution time in some areas were low while others were high. On the other hand, Health and Public Safety had the lowest average resolution time with a uniform distribution across all areas.

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
