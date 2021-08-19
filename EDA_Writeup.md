## **Using NYC MTA turnstile Data to Reduce Carbon Footprint**

Prathap Rajaraman

**Abstract**

The goal of this project is to locate neighborhoods that could use further investment in subway infrastructure such as tracks, lines, and new stations. To do this, I took ridership levels by station and after cleaning up and filtering the data appropriately, I mapped these stations to zip codes and neighborhoods and used census data to calculate ridership per capita by neighborhood. I then looked for neighborhoods that went below a pre-determined threshold and seeked patterns and trends. To do so, I built plots and charts to analyze my findings.



**Design**

The NYC Department of Transportation and Department of Environmental Protection wish to reduce carbon footprint and congestion of New York City roads. One way to do this would be to reduce the need for car ownership by adding to an already significant subway infrastructure. Currently, [less than half the city's inhabitants own cars](https://edc.nyc/article/new-yorkers-and-their-cars), but there is still room for growth as some neighborhoods/boroughs are better equipped than others.

To tackle this project, I used the [MTA turnstile dataset ](http://web.mta.info/developers/turnstile.html) to determine total ridership by subway station. For deeper analysis, I used Google API and geopandas to map stations to zip codes and coordinates, and used [population data by neighborhood](https://data.beta.nyc/dataset/pediacities-nyc-neighborhoods) to map to control for differences in neighborhood size. I wanted to see which areas are better equipped to handle the majority of its population going car-less and which ones have room for improvement. 

**Data**

As mentioned in my design, I will be using the MTA turnstile dataset as my main source of analysis, along with neighborhood population data. Each row contains entry and exit counts, split into 4 hour intervals, broken down by turnstile, time/day, and subway station. The following notes adds more color as to the scope of data in use for this project:

*Data Filtering*

1. The intervals used are June/July 2019 and June/July 2021. 2021 was used for the purpose of taking the latest and most relevant trends. Meanwhile, 2019 was used as a sanity check. I wanted to confirm that my findings are credible and not necessarily due to COVID-related measures.
2. Not all entries are created equal. The entries for a given station could potentially be attributed to leaving the house/apartment for work, leaving the office, returning from a restaurant/bar, and tourism, to name a few. This can lead to an apples to oranges comparison between stations, as some neighborhoods can have more of these attributes than others. To control for this, and because the goal of this analysis is to ultimately have more residents using the subway and less reliant on owning cars, I will be looking at subway entries on weekdays before noon. By normalizing this way, the entries seen in my analysis will be most likely due to morning commuters, and less likely due to other external factors, for all neighborhoods.

*Data Cleaning*

1. The `ENTRIES` column provided is cumulative, so I created a new column, `NEW_ENTRIES`, that takes the difference between entry counts at incremental time intervals.
2. Outliers and faulty data are corrected and removed.
3. To get to the end metric of total subway entries per station, I will be summing up entries from all turnstiles for a single station. The following fields will be grouped: `C/A, UNIT, SCP`. Then, the `NEW_ENTRIES`gets summed up for total entries for the mentioned time intervals.

*Data Mapping*

1. Google API is used to map stations to zip codes and coordinates.
2. Population data mentioned previously is used to map zip codes of stations to neighborhoods and neighborhood populations.



**Algorithms**

1. Taking the total entries for each subway station for a given time interval
2. Mapping each subway station to a neighborhood, and dividing by neighborhood population to determine neighborhood ridership per capita, and finding neighborhoods that fail to meet threshold
3. The threshold is 4.94 entries per capita post-COVID and 12.36 pre-COVID. The calculation for the threshold is the product of the following:
   1. We ideally want NYC residents to use the subway instead of a car to commute to work daily, so we will start with the ideal threshold of 40, which is one subway entry per day for two months worth of business days.
   2. [77% adult population](https://www.baruch.cuny.edu/nycdata/population-geography/age_distribution.htm) that would commute to work
   3. [55%](https://edc.nyc/article/new-yorkers-and-their-cars) of NYC residents do not own a car. However, this varies by neighborhood so ideally, we would like to get to the 55% threshold for neighborhoods that fail to meet it.
   4. Of those car owners, [73%](https://edc.nyc/article/new-yorkers-and-their-cars) use their car for commuting, as opposed to keeping it for miscellaneous purposes such as weekend trips.
   5. For 2021 only, a COVID adjustment of 40%. I am assuming that in a post pandemic world, a hybrid or fully remote work arrangement is fully embraced.



**Tools**

- Pandas for data manipulation
- SQL Alchemy for importing MTA data
- Google API, geopandas, and geopy for location mapping
- Matplotlib, Seaborn, and Plotly for visualization



**Communication**

A brief deck on my exploration and analysis, along with visualizations. Please see below for a snapshot of my results. The larger the dot, the smaller the ridership is for those neighborhoods and the greater the need for investment.

![](/Users/prathaprajaraman/Documents/Data_Science/Metis/EDA/MTA_project/Plots/NYC_mapplot.png)