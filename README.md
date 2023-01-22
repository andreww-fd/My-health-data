# My health data analysis project. 
### Data source: Phone (Apple HealthKit Technology)

Data for this project was exported from Health app on my phone in .xml format. Initial file consisted of more than 120.000 rows of data starting from 2021-02-27 to 2022-12-30. File with raw data is not included since I do not want to share all this personal information.

The goal of the project is to use Python to analyse my own health data and build some visualizations which can possibly help me better understand my activity levels and pinpont key indicators to work on and improve.

Data file has 25 columns but I will be using only 8 of them in this analysis. Apart from removing missing data and changing data types, all values from "type" column where transformed. For instance all values had common prefix "HKQuantityTypeIdentifier" that was redundant and deleted: **HKQuantityTypeIdentifierStepCount -> StepCount**
![image](https://user-images.githubusercontent.com/102311131/213932440-e8bdb951-8a9e-4183-ae38-acfe630e97a7.png)

The last transformation step was aggregating data by day. Some values such as "HeadphoneAudioExposure" level need to be aggreagated using .mean(), since we want to see an average dB value per day while other values such as "StepCount" need to be aggregated using .sum() since to see total steps made per day, so we use .sum() in this case. To make right aggregations two separate datasets where created **grouped_data_mean** and **grouped_data_sum**. These two data files can be found in data folder.
![image](https://user-images.githubusercontent.com/102311131/213932414-9aeff5c5-3844-41a1-8239-f47f81e72b39.png)

In terms of visualizations I used lineplot with original data plotted as well as its MA. Moving average helped me smooth out the outliers and get a much better looking graph that is easier to understand. In addition I added horizontal lines representing mean values or, in case of audio exposure levels, lines that can help me see whether my music listening volume is low enough and not dangerous to my hearing.
![download](https://user-images.githubusercontent.com/102311131/213932949-70491554-10aa-4a2c-8891-e3d440b7862b.png)
Speaking of my steps count I can definitely see that for the last couple of month my activity is below my average and this is probably one of the areas I need to work on :D .
![download](https://user-images.githubusercontent.com/102311131/213933347-66996315-19d0-4195-9c2f-c5a395145ac3.png)

