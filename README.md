# A Demographic Exploration of Farmers Markets in the US

Udacity Data Science Nanodegree - Project 1
Max Sydow


## Overview
Farmers markets appear all over the US, and can provide an alternative to traditional grocery stores for obtaining fresh food and other services from local sources. The aim of this project is to explore accessibility to such markets. Python packages such as Pandas and Numpy were used in a [Jupyter notebook](./FarmersMarkets.ipynb) to analyze the data sets.  Matplotlib was used for visualization, and Sklearn was used for linear regression.  County level data is examined to answer questions such as:

1.  Which counties have the highest and lowest concentration of farmers markets?
2.  Does income relate to accessibility to markets?
3.  Is population density related to concentration of farmers markets?
3.  Does higher average income influence the number and type of offerings?


The data used here can be found from Kaggle, and pose the question of accessibility to farmers markets in the US. 

https://www.kaggle.com/madeleineferguson/farmers-markets-in-the-united-states

Two data sets are used. A farmers market set includes data on farmers markets by county, including market names and food offerings. This data set can be obtained from: 

https://www.ams.usda.gov/local-food-directories/farmersmarkets

The county data set includes more general demographic information like population and incomes, it can be found at: 

https://en.wikipedia.org/wiki/List_of_United_States_counties_by_per_capita_income

The data set csv's used here were downloaded directly from the data tab on the Kaggle site.


## Data Summary

The Farmers Market data set has 8804 rows and 59 columns.  The county set has 3233 rows and 8 columns.  Duplicate and null values for county were found in each data set and were removed.  An integer was used as an identifer for county in the county dataset, but some counties had a '—' instead.  It was found that these counties are in US territories.  They were also removed to allow use of _number_ as a unique identifier, thus only US states were considered.  The 2 sets were joined on the _State_ column that both had in common.  A new column, _StateCounty_, was created to concatenate _State_ and _County_ in order to make rows in this column consistent across the joined set.  

## Highest/Lowest Concentration of Farmers Market by County.

The top 10 counties with the most farmers markets are:

- California, Los Angeles       128
- Illinois, Cook                110
- Massachusetts, Middlesex       60
- Massachusetts, Worcester       59
- California, San Diego          49
- Pennsylvania, Philadelphia     49
- Minnesota, Hennepin            48
- Washington, King               44
- Hawaii, Honolulu               43
- Wisconsin, Dane                42

The bottom 10 counties with the least farmers markets are:

- South Carolina, Dorchester    1
- Georgia, Ware                 1
- Oklahoma, Muskogee            1
- Arkansas, Yell                1
- Illinois, Edgar               1
- Texas, Jasper                 1
- Kentucky, Metcalfe            1
- Mississippi, Union            1
- Georgia, Jasper               1
- North Dakota, Wells           1

The counties with the most farmers markets seem to be relatively highly populated, so I wanted to see if the most populated counties indeed do have higher numbers of farmers markets.  Comparing tables of counties ordered by population and by count of farmers markets (_FMID_count_) can shed some light.

<table>
<tr><th>Ordered by Population </th><th>Ordered by FMID_count</th></tr>
<tr><td>

|StateCounty | Population | FMID_count|
|--|--|--|
|California, Los Angeles| 9893481|128 |
|Illinois, Cook |5212372| 110|
| Texas, Harris | 4182285 | 16 |
| Arizona, Maricopa | 3889161 | 40 | 
| California, San Diego | 3138265 | 49 |
| California, Orange | 3051771 | 27 |
| Florida, Miami-Dade | 2549075 | 33 | 
| New York, Kings | 2539789 | 37 |
| Texas, Dallas | 2412481 | 11 |
| New York, Queens | 2256400 | 18 |

</td><td>

|StateCounty| Population | FMID_count | 
|--|--|--|
|California, Los Angeles| 9893481|128 |
|Illinois, Cook |5212372| 110|
| Massechusetts, Middlesex | 1522533 | 60 |
| Massechusetts, Worcester | 802688 | 59 |
| Pennsylvania, Philadelphia | 1536704 | 49 |
| California, San Diego | 3138265 | 49 |
| Minnesota, Hennepin | 1170623 | 48 |
| Washington, King | 1974567 | 44 |
| Hawaii, Honolulu | 964678 | 43 |
| Wisconsin, Dane  | 496762 | 42 |

</td></tr> </table>


It appears that only 3 of the most populous counties overlap with the list of counties with the highest number of farmers markets. So it would seem that there are a lot of highly populated counties with a relatively low concentration of farmers markets. Harris county, Texas appears to be the most noticable outlier in this regard. However, counties with the most farmers markets are still fairly large with most having populations close to or above 1 million.  Dane county Wisconsin sticks out as being less populated in this list.  There is an absence of mainland US southern states here.  Perhaps farmers markets are more popular on the coasts and upper midwest.  King, Hennepin, Dane, and Worcester counties all contain cities that would describe themselves as more educated and liberal leaning.  Further investigation might show that this is more than a coincidence, but education levels and political affiliation and other such lifestyle characteristics are not included in this data.  

More general population trends will be explored later.
