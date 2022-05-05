# Machine Learning Project

# Part-1
- Go to [Part 2](#Part-2)

- Iowa Liquor Sales: [Dataset Link](https://www.kaggle.com/datasets/gabrielramos87/iowa-sales-liquor-jan-2021jan-2022)

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

### heatmap - (Category Transactions by Weekday)
- There is a high transaction rate of products on Tuesday and Friday throughout the months in the year
- January had the highest amount of transactions in categories ordered followed by December
- Sunday and Saturday contain anomalies
  - Iowa requires different vendor licenses to buy on weekends
  - Data points could be dropped to reinforce a trend

![](https://i.imgur.com/aO3nc5z.png)

### histplot (Pack Popularity by Category)
- Most packs tend to hover around the 6-24 size
- Outliers of high packs ordered, only two instances of 120
- Subsequent orders of a customer may contain the same pack size for a certain category
- Data indicates 12 as the most frequent pack size

![](https://i.imgur.com/6Dvzq1e.png)

## Summary of Part 1 (Category Column)
Prediction of the next purchase category seems feasible with the findings. Data could be subset into vendors to examine their high purchase products as some have higher popularity—American Vodka and Canadian Whiskey are among the top in transactions. For 2021, January and December were the most active in category transactions, with the highest unique transactions occurring on Tuesday and Friday. The pack quantities seem to focus around the twelve-pack and six-pack. The next category ordered can likely be predicted based on this information's historical data.

# Part-2

## Data Distributions
- Similar to previous findings
  - Certain categories highly popular (i.e. American Vodkas)
  - Similar trends in volume sold in each category
    - Small variations as volume is not equivalent to transaction occurrences
- Outliers still present in large order sizes
- Weekend sales data is much smaller due to state regulation
  - Potentially drop for higher accuracy

## Aggregations
- Grouping by `category_name`
- Mean, min, and max are used to evaluate the patterns of previous orders based off of:
  - `bottles_sold`
  - `packs`

## Justifications

### Data Sanitation
- Dropping:
  - redundant location information
  - unique identifiers
    - Possible preservation of vendor ID for recurring prediction purchases
  - item string descriptions 
  - any null entries at that point
    - Minimal loss in entries since unneeded columns contained the majority of NA values
  - categories with less than 1000 entries
    - Top categories peak at nearly 400K entries
    - Removing categories with a lower transaction rate may help improve accuracy

### Encoding of Strings
- Liquor categories and counties will be one-hot encoded
  - May add a column overhead
  - Will be more descriptive by not giving an imposed ordinal value
  - Category and county should represent subsets of product clusters with no bias

### Splitting X and Y Data
- Features will be the remaining data to potentially find identifiers
  - Pack size
  - Bottles sold
  - Volume
  - County trends
  - etc.
- Label will be the category of the liquor
  - The goal will be to predict which one will come next

