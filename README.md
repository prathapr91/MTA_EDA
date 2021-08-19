## **Project Proposal Template**

 

**Background**

New York City has such a robust subway system that it is in a unique position where less than [half its inhabitants own cars](https://edc.nyc/article/new-yorkers-and-their-cars). However, there is still room for improvement as there are areas that could use more investment in infrastructure. The purpose of this exploratory data analysis is to pinpoint neighborhoods that have low ridership per capita. The New York Department of Transportation can use this information to gauge which neighborhoods warrant more investment in subway lines, stations, and tracks. By having more New York City residents utilize the subway system in a convenient manner, more residents will benefit financially by not feeling obligated to purchase a car and the city will benefit from reduced congestion and a smaller carbon footprint.

 

**Data Description**

·   I will be looking at the [MTA weekly turnstile data](http://web.mta.info/developers/turnstile.html) from June – July 2021. Each row contains a count of the number of people who entered or exited a given subway station, broken down in 4-hour intervals.

·   Because some neighborhoods are more crowded than others, we should expect them to have more usage. For example, subway usage in Midtown Manhattan is bound to be significantly greater than that of neighborhoods in other boroughs. To control for this, I will be utilizing [population data by neighborhood](https://data.beta.nyc/dataset/pediacities-nyc-neighborhoods) so that I can conduct analysis based on subway usage per 1000 inhabitants rather than a nominal value.

·   A unit of analysis for this project will be a given neighborhood’s total ridership per capita.

 

**Tools**

·   I am using SQL, Pandas, and Matplotlib/Seaborn in my work for data analysis, manipulation, and visualization.

·   I will also be using Google API and GeoPandas for location mapping

 

**Work Location**

·   **EDA_Deck.pdf**:  High level summary of my analysis

·   **EDA_Writeup.md**: Detailed writeup of methodology and analysis

·   **EDA_Code.ipynb**: Underlying Python code used