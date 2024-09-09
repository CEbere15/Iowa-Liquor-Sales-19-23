# Iowa Liquor Sales Data (2021)
### Table of Contents


## Overview
### Summary

In the state of Iowa, the state government acts as the sole wholesaler and distributor of distilled spirits through its Alcohol and Tax Operations Division, a branch from the Iowa Department of Revenue. Along with managing the sale to licensed businesses in the state. Meaning they buy 

### Data Source
### Tools

### Data Dictionary
| Column       | Data Type       | Description                              |
|-------------------|-------------|-----------------------------------------------------------------------------|
| `Invoice/Item Number`      | Text     | Index for the orders.                        |
| `Date`    | 	Datetime | Date that the order was made.     |
| `Store Number`      | Integer     | Unique identifier for the store who made the order.                |
| `Store Name`      | Text     | Name of store who made the order.                   |
| `Address`      | Text     | Address of the store's location.  |
| `City`   | Text   | The city that the store is located in.|
| `Zip Code` | Integer     | Zip code where the store is located in.           |
| `Store Location`      | Point     | Coordinates for the point in which the store is located in.|
| `County Number`      | Integer     | Number for the Iowan county that the store who ordered the liquor is located in.|
| `County`      | Text     | Name of the Iowan county that the store who made the order is located. |
| `Category`      | Integer     | Unique code for the type of liquor ordered.  |
| `Category Name`      | Text     | Name of the type of liquor ordered. |
| `Vendor Number`      | Integer     | Code for the vendor who made the brand of liquor.   |
| `Vendor Name`      | Text     | The name of vendor who made the brand of liquor.  |
| `Item Number`      | Integer     | Number associated with the liquor product ordered.  |
| `Item Description`      | Text     | Description of the liquor product that was ordered.   |
| `Pack`      | Integer     | Number of bottles in a case for liquor ordered.   |
| `Bottle Volume (ml)`      | Integer     |Volume in milliliters of each liquor bottle ordered   |
| `State Bottle Cost`      | Integer     | The cost the Iowan Alcoholic Beverages Division paid for each bottle ordered |
| `State Bottle Retail`      | Integer     | The amount the store paid for each bottle of liquor ordered from the state   |
| `Bottles Sold`      | Integer     | Number of bottles ordered by the store   |
| `Sale (Dollars)`      | Integer     | Total cost of the order (number of bottles multiplied by the state bottle retail)  |
| `Volume Sold (Liters)`      | Integer     |Total volume in liters sold from the order  ((Bottle Volume (ml) x Bottles Sold)/1,000)   |
| `Volume Sold (Gallons)`| Integer |Total volume in gallons sold from the order ((Bottle Volume (ml) x Bottles Sold)/3785.411784)|



### Objectives
- Identify overall sales trends for the year
- Identify how geography affects sales
- Find which products are purchased together the most, through market basket analysis
- Categorize stores based on their purchasing behavior
- Identify the Department of Revenue's pricing strategies
- Study which vendors and products produce the products most profitable for the IDR
### References


## Data Cleaning and Preparation


## Exploratory Data Analysis

### Descriptive Statistics


### Sales Trends

### Geographical Distribution of Sales

### Category and Product Analysis

### Products vs. Revenue

## Data Analysis

### Vendor Performance Analysis

### Category-Specific Analysis

### Customer Segmentation


#### RFP Analysis



#### Geographical Sales Performance Analysis

#### Revenue by City
With stores segmented by location and the amount of revenue produced, we can look at which cities' stores brought the most revenue
```py

# Grouping by revenue by cities
CityRevenue = data.groupby('City').agg({
    'TotalRevenue': 'sum',  # Total revenue per city
    'Bottles': 'sum'        # Total bottles sold per city
}).reset_index()

# Sorting by cities that generated the most revenue
CityRevenue = CityRevenue.sort_values(by='TotalRevenue', ascending=False)

# Create a bar graph that shows the Top 50 Iowan cities by revenue
CityRevenue.head(50).plot.bar(x='City', y='TotalRevenue', rot=0, figsize=(75,50))
```


![Top 50 Cities by Revenue](https://github.com/user-attachments/assets/13fc3207-c952-41b9-bf2c-d977d234df51)

</br>

### Profit Markup and Margin Analysis

#### Category Profit Analysis
```py
plt.figure(figsize=(30,80))


data.boxplot(column='Profit', by='CategoryName', vert=False, grid=False, figsize=(40,30))



plt.title('Profit by Category')
plt.xlabel('Profit')
plt.ylabel('Category')
plt.show()
```

</br>

![Category Profit](https://github.com/user-attachments/assets/2ec4c5a7-5faa-4d53-a6bf-9129c42fa8f2)

Cost by Category
```py

plt.figure(figsize=(30,80))


data.boxplot(column='Cost', by='CategoryName', vert=False, grid=False, figsize=(40,30))



plt.title('Cost by Category')
plt.xlabel('Cost')
plt.ylabel('Category')
plt.show()
```
</br>

![Cost by Category](https://github.com/user-attachments/assets/cebc4793-69de-4143-b932-b53cf6546337)


### Market Basket Analysis

## Results
### Limitations

## Licenses




