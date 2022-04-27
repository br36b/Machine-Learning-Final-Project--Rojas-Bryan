# Machine Learning Project
Iowa Liquor Sales: [Dataset Link](https://www.kaggle.com/datasets/gabrielramos87/iowa-sales-liquor-jan-2021jan-2022)

## Overview
-----------
This dataset represents the sales of liquor from the Iowa Alcoholic Beverage Division to licensed Iowa vendors. The division regulates the traffic and distribution of all alcoholic beverages; the dataset contains various details from product and establishment transactions across the state.  

## Data Descriptions
---------------
- 2805307 rows
- 24 columns

## Potential Columns of Interest
-----------------
| Column | Value of Research |
| ------- | -------- | 
| `date` | Could offer dates of high sales in the year |
| `store_number` | Track highest sales of a particular store by grouping |
| `category` | Product trends within category may provide stock insights |
| `sale_dollars` | Useful to general information of high, low, and average sale amounts |
| `state_bottle_cost` & `state_bottle_retail` | Useful to calculate the profits on state/vendor transactions |

### Potential Cleaning
There are columns that provide redundant information about location that can be dropped.
It may also be beneficial to drop the string names for product/vendor analysis. These already contain equivalent numerical identifiers.

-----------------
### pairplot
- Not many strong correlations found within variables

![](https://i.imgur.com/3JgBZa3.png)

### lmplot - Volume (Gallons) vs Sales (Dollars)
- As more gallons are sold, sales sold increased
- Potential outliers exist where a certain products are high volume and high profit and vise-versa
  - Worthwhile to find best volume to sale profit ratio

![](https://i.imgur.com/I5FPtfx.png)

### lmplot - Volume (Gallons) vs Bottles Sold
- More volume tends to result in more bottles used
  - Nothing strong for comparison
  - Appears that some bottles may hold more or less than others

![](https://i.imgur.com/xhmkw8B.png)

## Relationships by Product Categories
### countplot - (Count of Each Category)
- Very clear product favoring
  - Top Sellers Found:
    1. American Vodka was the best seller
    2. Canadian Whiskies was the second best
    3. Light Bourbon Whiskeys
- Predicting the category of the next transaction could be interesting
  - Date combinations with the frequency of bottle/pack counts could optimize product prediction

![](https://i.imgur.com/1Q0CnTz.png) 

### heatmap - (Category Diversity by Weekday)
- There is a high variety of products on Tuesday and Friday throughout the months in the year
- January had the highest amount of variety in categories ordered followed by December
- Sunday and Saturday contain anomalies
  - Iowa requires different vendor licenses to buy on weekends
  - Data points could be dropped to reinforce a trend

![](https://i.imgur.com/DLZ7pjn.png)

### histplot (Pack Popularity by Category)
- Most packs tend to hover around the 6-24 size
- Outliers of high packs ordered, only two instances of 120
- Subsequent orders of a customer may contain the same pack size for a certain category
- Data indicates 12 as the most frequent pack size

![](https://i.imgur.com/6Dvzq1e.png)

## Summary (Category Column)
Prediction of the next purchase category seems feasible with the findings. Data could be subset into vendors to examine their high purchase products as some have higher popularity—American Vodka and Canadian Whiskey are among the top in transactions. For 2021, January and December were the most diverse in category selection, with the highest unique categories occurring on Tuesday and Friday. The pack quantities seem to focus around the twelve-pack and six-pack. The next category ordered can likely be predicted based on this information's historical data.