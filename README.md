# PyBer_Analysis

## Overview

Access the complete [Analysis](https://github.com/Lan-kdl/PyBer_Analysis/blob/main/PyBer_Challenge.ipynb) with code and DataFrames

The pupose of this analysis was to provide PyBer with the information needed to make decisions relating to the price of fare for ride-sharing services. To perform this analysis, I used [ride_data_csv](https://github.com/Lan-kdl/PyBer_Analysis/blob/main/Resources/ride_data.csv) and [city_data_csv](https://github.com/Lan-kdl/PyBer_Analysis/blob/main/Resources/city_data.csv) which, when merged, included data regarding driver, rider, and fare information by city type (Urban, Suburban, Rural). I retrived the total rider count, total driver count, and the sum of total fares.

![totalrides_drivers_fares](https://user-images.githubusercontent.com/95589611/152712015-f784597e-4de6-4ecf-b775-ca17a649a96a.png)

These were used to calculate the average fare per ride and average fare per driver. 

![average_fare_rides_drivers](https://user-images.githubusercontent.com/95589611/152712045-c9d7fc88-7cd0-4375-be13-1f2029e39516.png)

I turned these series into a DataFrame using the pd.concat() method.

![clean_data_frame](https://user-images.githubusercontent.com/95589611/152712074-3388f60e-cb02-44cf-bb77-055ab92bc09d.png)

Code for converting multiple series into a DataFrame came from [StackOverflow](https://stackoverflow.com/questions/18062135/combining-two-series-into-a-dataframe-in-pandas).
We then cleaned and formated the DataFrame. The results of this analysis can be seen [here](https://github.com/Lan-kdl/PyBer_Analysis#results). 

I also created a plot from which to view the total weekly fares for each city type. Once again, I used the merged data from [ride_data_csv](https://github.com/Lan-kdl/PyBer_Analysis/blob/main/Resources/ride_data.csv) and [city_data_csv](https://github.com/Lan-kdl/PyBer_Analysis/blob/main/Resources/city_data.csv) to create the multi-line graph. I first calculated the sum of fares for the city type and date. 

![new_df](https://user-images.githubusercontent.com/95589611/152712362-dbd28e9c-8c06-4dd2-9588-ed86f4da613f.png)

I cleaned the DataFrame and then used the loc() method to retrieve the data from 2019-01-01 to 2019-04-29. 

![pivot_df](https://user-images.githubusercontent.com/95589611/152712419-1ce6b604-e589-4c7d-a1fc-34fc1d1ad329.png)
![loc_date](https://user-images.githubusercontent.com/95589611/152712426-c24883c4-5f58-4c62-9260-ced56dba30b6.png)

I got the sum of fares for each week by using resample("w") and sum() which gave me the following output. 

![resample_w](https://user-images.githubusercontent.com/95589611/152712442-a0d5c387-5821-4eb1-8ac4-85b356999366.png)

This is the DataFrame that I used to create the multi-line plot. The results of this analysis can be seen [here](https://github.com/Lan-kdl/PyBer_Analysis#results). 

## Results

### PyBer Summary 

![Correct_Summary_DF](https://user-images.githubusercontent.com/95589611/152713132-f39f5b38-257b-4339-82d5-467ed831eff4.png)

As can be seen from the summary DataFrame above, Urban cities have both the most riders and drivers out of the three city subtypes. This explains why they have the greatest sum of fares even though they spend the least on ride-sharing per ride. Rural cities have the highest fare per ride and als per driver. Even though Suburban cities have 6x total rides in comparison with Rural which has the least, their fare is only  $3.65 less per ride; Whereas Urban total riders is only 2.6x that of Suburban cities and their fare per ride is $6.44 less Suburban fare per ride. 

### Sum of Fare Per Week by City Type

![PyBer_fare_summary](https://user-images.githubusercontent.com/95589611/152712509-eb9e05fc-19d2-4621-910a-912ab9064370.png)

As can be seen in the visualization above, Rural cities had the least total fare per week during Jan, 1, 2019 and April 29, 2019, peaking around $500 in the first week of April. The city type with the most expensive fare during this time period was the Urban city type which peeked multiple times during the four months near $2,500. It should be noted that whereas the Suburban and Urban city types increased steadily in the first weeks of January, the Rural city type faced a decrease in fares during the first week of January. 

## Summary

To rectify the discrepencies between the city types I have three reccomendations: 

### Decrease the fare given to the driver per ride for Rural cities. 
The average fare for drivers per ride for Suburban cities is only 7% of the average fare per rider, and the average fare per driver for Urban cities is even less, at 3% of the average fare per rider. Meanwhile, the drivers for Rural cities make 23% of the average fare per rider. To make the drivers make closer to the same amount per drive, I suggest to increase the fare made by drivers of Urban cities and decrease the fare made by drivers in Rural cities. You may be able to decrease the fare of Rural drivers by hiring more rural drivers as there are 16x the number of drivers in Suburban cities. 

### Increase the price of Urban Fare
The average fare price for Rural city fare is the highest, but it also has the least amount of riders. Suburban cities have 5x the riders than Rural cities and their fare price is $3.65 less than riders in Rural cities. Meanwhile, Urban cities only have 2.5x more riders than Suburban cities and their average fare per ride is $6.44 less than the average Suburban fare per ride. I suggest increasing the Urban price of fare by $4.61 so that there price is only $1.83 less than that of Suburban fare and more in line with the increase in total rides. 

### Constuct fare price that fluxuates with busiest and slowest month. 
With many ride-sharing apps, the price of the ride changes with distance and time of day. I suggest also modifying the price during slow and busy months so that the sum of fares per week is more stable. For example, there is a discrepency in the Rural city data where they experience a decrease in total fare during Jan. I solution would be to raise the price of fare during the holiday seasons. Suburban cities have a sharp decrease in total fares at the end of February from which they have a hard time recovering until the summer break. A solution would be to increase the price of fare during spring break. To compensate for the increase in prices during these periods, it would be safe to decrease the price of fare in celebration of the new year or summer months where most cities are experiencing increases or stabilizations of total fare. 
