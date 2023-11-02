# Preliminary Analysis

![311graph1](https://github.com/BU-Spark/ds-boston-311-tracker/assets/126114871/36878e1e-d584-467f-9f9e-9828fc74636e)
![311graph2](https://github.com/BU-Spark/ds-boston-311-tracker/assets/126114871/c95910ba-aa2a-48ef-baa2-f1f79bf96a8e)
![311graph3](https://github.com/BU-Spark/ds-boston-311-tracker/assets/126114871/0349fbad-0b4c-485f-ae48-0127cefc90e4)
![311graph4](https://github.com/BU-Spark/ds-boston-311-tracker/assets/126114871/97d3560f-53d4-4d5f-8ab1-bcc135067e0f)

# Base Questions

## Some Prior Information

Since the entries in data are incosistent and we had to modify a few things

1. Added Resolution Time Column
2. Changed all negative values in Resolution Time column to be equal to 0
3. Combined NAN and ' ' (space character string) value in neighborhoods into one unique name 'No Neighborhood Data'
4. For questions that invlove QUEUE, we had to apply custom grouping for queues in PWDx department, where needed. (The Group Name was a keyword that appeared the most in distinct queues, i.e. group district invloves all the queues where district was the dominant keyword)

### PowerBI

#### Link to PowerBI Report

Link: <https://app.powerbi.com/reportEmbed?reportId=41b83596-6c42-48c1-9d28-9b7e48622637&autoAuth=true&ctid=8826d2d1-cf01-4ed7-8ba7-baa6f836f7a5>

#### PowerBI Comments

PowerBI work was done by a different memeber, and some slight differences in data processing still exist.

1. Resolution time column exists, but it is a double type column, that refers to days. Negative values are still changed to 0.
2. Queue grouping was not changed.
3. The text in closure reason was changed to a single word based on a combination of data exploration and the provided data dictionary.

## What is the total volume of requests per year, or how many 311 requests is the city receiving per year?

![](graphs/volume_per_year.png)

## Which service requests are most common for the city overall AND by  NEIGHBORHOOD and how is this changing year over year by SUBJECT (department), REASON,QUEUE?

### Overall

![](graphs/top_10_overall.png)

### By Neighborhood

![](graphs/most_common_by_neighborhood.png)

### By SUBJECT

![](graphs/yearly_top_subject.png)

### By REASON

![](graphs/yearly_top_reason.png)

### By QUEUE

![](graphs/yearly_top_queue.png)

## How is the case volume changing by submission channel SOURCE?

![](graphs/volume_by_source.png)

## What is the average # of daily contacts by year?

![](graphs/yearly_day_average.png)

## Volume of top 5 request types (TYPE) 

![](graphs/top_5_type.png)

## Average goal resolution time by QUEUE

![](graphs/average_resolution_time_queue.png)

## Average goal resolution time by QUEUE and neighborhood

![](graphs/average_resolution_time_queue_and_neighborhood.png)

## What % of service requests are closed (CLOSED_DT or CASE_STATUS) vs. no data (CASE_STATUS = null) vs. unresolved (CASE_STATUS = open)?

### Overall
![](graphs/open_vs_closed_total.png)
### By Year 
![](graphs/yearly_open_vs_close.png)
### By Year (proportion)
![](graphs/yearly_open_vs_closed_proportion.png)


