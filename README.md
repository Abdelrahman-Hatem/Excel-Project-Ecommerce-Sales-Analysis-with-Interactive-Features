# E-commerce Sales Interactive Dashboard

## 1 - Business Overview:
The E-commerce Sales Interactive Dashboard is designed to provide comprehensive insights into the sales performance and customer behavior of a bicycle and accessories company. Leveraging Power Query, Power Pivot, and DAX in Excel, the dashboard integrates data from various sources, including customer information, product details, sales records, territories, sales reps, and shipping methods.

## 2 - Introduction:
In the fast-paced world of e-commerce, understanding customer behavior and sales trends is critical for sustaining business growth. Our case study delves into the creation of a dynamic and interactive Excel dashboard tailored for a thriving bicycle and accessories company. The goal is to leverage data analytics tools such as Power Query, Power Pivot, and DAX to transform raw data into actionable insights.

## 3 - Objectives:
- Enhance Decision-Making: Utilize data insights to improve decision-making by understanding customer behavior, identifying top-performing products, and optimizing resource allocation for sustained business growth.

## 4 - Data Overview:

### Customers:
- **Number of Customers**: Includes information about customers, such as demographics, income, and the date of their first purchase.
- **Demographics**: Provides details like gender, marital status, education, and occupation.
- **Income Distribution**: Information on the yearly income of customers.
- **House Ownership**: Indicates whether customers own a house.

###  Products:
- **Number of Products**: Contains a variety of products, each identified by a unique key.
- **Product Categories**: Categorized by subcategory and category.
- **Attributes**: Product attributes include color, size, style, and class.
- **Pricing**: Information on standard cost, list price, and dealer price.

### Sales:
- **Sales Transactions**: Detailed information about each sale, including order details, product information, and customer details.
- **Quantity and Prices**: Data on order quantity, unit prices, and extended amounts.
- **Discounts**: Information on discounts applied to products.
- **Costs**: Standard costs, total product costs, tax amounts, and freight charges are included.
- **Dates**: Order and shipment dates are provided.
- **Shipping and Sales Reps**: Information on the chosen shipping method and the responsible sales representative.

###  Territories:
- **Geographic Distribution**: Territories are defined, including information about states, countries, abbreviations, and continents.

### Sales Reps:
- **Sales Representatives**: Information on sales representatives, each identified by a unique ID.

###  Shipping Methods:
- **Shipping Options**: Different shipping methods are available, each identified by a unique ID.


# 5 - Data Preparation:

##  Calendar Table Creation:

#### Calendar Table Creation Process:
- Reference the sales table in Power BI.
- Identify the earliest and latest dates using DAX functions (MIN, MAX).
- Create a calendar table using the identified date range with the CALENDAR function.
- Remove unnecessary columns for efficiency.

####  Drill Down for Value:
- Utilize the generated list to drill down into sales data.

####  List of Dates Creation:
- Use the DAX formula {number.from(earliestDate)..Number.From(latestDate)} to create a list of dates.
- Analyze data at different levels (day, week, month) based on the calendar.

#### Creation of Relationships Between Tables:
![image](https://github.com/Abdelrahman-Hatem/Excel-Project-Ecommerce-Sales-Analysis-with-Interactive-Features/assets/60587162/c204c1a3-3bd5-45be-a20b-3a58c13ef337)

# 6 - Power Pivot and DAX:

## Creating Explicit Measures Using DAX:

### First Measure: Daily 12 Month Sales Moving Average

#### Explanation:
- This measure calculates the moving average of the 'Sales Amount' over the last 12 months.
- It uses the AVERAGEX function to iterate over each day in the date context and calculates the average of 'Sales Amont.'

![image](https://github.com/Abdelrahman-Hatem/Excel-Project-Ecommerce-Sales-Analysis-with-Interactive-Features/assets/60587162/3afb0f2c-6237-4677-a055-7b0c3f427de5)


### Second Measure: Avg Sales Per Occupation
![image](https://github.com/Abdelrahman-Hatem/Excel-Project-Ecommerce-Sales-Analysis-with-Interactive-Features/assets/60587162/2df0a6a7-53e6-40a1-9b21-27ed51946641)

#### Explanation:
-	This measure calculates the average sales per customer based on their occupation.
-	It uses a VAR block to calculate the number of customers and sales for a specific occupation and then divides them to get the average.



### Third Measure: Avg Shipping Price
- **Formula Explanation:** `Avg Shipping Price = AVERAGE(Sales[Freight])`
- **Explanation:** This measure computes the average shipping price across all sales transactions.

### Fourth Measure: Freight Cost
- **Formula Explanation:** `Freight Cost = SUM(Sales[Freight])`
- **Explanation:** This measure computes the total freight cost for all sales transactions.

### Fifth Measure: Freight/Cost %
- **Formula Explanation:** `Freight/Cost % = DIVIDE([Freight Cost],[Product Cost])`
- **Explanation:** This measure calculates the percentage of freight cost relative to the total product cost.

### Sixth Measure: Product Cost
- **Formula Explanation:** `Product Cost = SUMX(Sales, Sales[OrderQuantity] * Sales[ProductStandardCost])`
- **Explanation:** This measure computes the total cost of products by multiplying the order quantity with the standard cost for each sale and then summing them up.

### Seventh Measure: Profit
- **Formula Explanation:** `Profit = [Sales Amount] - [Product Cost] - [Freight Cost]`
- **Explanation:** This measure calculates the profit by subtracting the total product cost and freight cost from the total sales amount.

### Eighth Measure: Sales Amount
- **Formula Explanation:** `Sales Amount = SUMX(Sales, Sales[OrderQuantity] * Sales[UnitPrice])`
- **Explanation:** This measure computes the total sales amount by multiplying the order quantity with the unit price for each sale and then summing them up.


# 7 -	Dashboard Components: 
https://github.com/Abdelrahman-Hatem/Excel-Project-Ecommerce-Sales-Analysis-with-Interactive-Features/assets/60587162/b8cee66f-9789-4d9b-bd50-36cfc720258a

# Dashboard Components:

#### 1. Daily 12 Month Sales Moving Average (Line Chart):
- **Description:** Displays a line chart representing the daily 12-month moving average of sales.
- **Purpose:** Helps identify trends and patterns in sales over time.

#### 2. Top 10 Products by Freight/Cost % (Bar Chart):
- **Description:** Illustrates the top 10 products with the highest freight cost as a percentage of product cost.

### 3. Average Shipping Price per Shipping Method (Column Chart):
- **Description:** Depicts the average shipping price for each shipping method using a column chart.
- **Purpose:** Allows a quick comparison of shipping costs associated with different shipping methods.

#### 4. Freight/Cost (Line Chart):
- **Description:** Represents the trend of total freight cost over time using a line chart.

### 5. Avg Sales per Occupation (Bar Chart):
- **Description:** Displays a bar chart presenting the average sales per customer for each occupation.

#### 6. Top 10 Products by Profit (Bar Chart):
- **Description:** Highlights the top 10 products with the highest profitability using a bar chart.

#### 7. Sales per Sales Rep (Column Chart):
- **Description:** Provides a column chart showing the total sales attributed to each sales representative.

#### 8. Profit Per State (Map Chart):
- **Description:** Utilizes a map chart to visualize profits across different states.
- **Purpose:** Offers a geographical perspective on profitability, helping identify regions contributing most to profit.


# Slicer Functionality:

#### 1. Year Slicer:
- **Functionality:** Allows users to filter the dashboard data by selecting a specific year.
- **Purpose:** Enables a focus on sales trends, product performance, and other metrics for a particular year.

#### 2. Product Category Slicer:
- **Functionality:** Permits users to filter the data by selecting a specific product category.
- **Purpose:** Facilitates a targeted analysis of sales, profitability, and shipping costs for a chosen product category.

#### 3. Sales Rep Slicer:
- **Functionality:** Enables users to filter the data by selecting a specific sales representative.

#### 4. Shipping Method Slicer:
- **Functionality:** Allows users to filter the data by selecting a specific shipping method.

# 9 - Dashboard Summary:

The E-commerce Sales Analysis Dashboard offers a comprehensive view of sales performance, cost structure, and profitability. Users can interact with the slicers to tailor the data to their specific needs, allowing for deep insights into different aspects of the business. The combination of charts and slicers provides a user-friendly interface for effective decision-making and strategic planning. The dynamic nature of the dashboard ensures that users can explore trends, identify key products, and assess the impact of various factors on overall sales and profitability.


# 10 - Business Impact:

- **Product Focus:** Concentrate efforts on high-profit and top-selling products for increased revenue.
- **Targeted Marketing:** Tailor marketing strategies based on customer occupations and preferences for improved engagement.
- **Efficient Logistics:** Optimize shipping methods to enhance efficiency and reduce costs.
- **Sales Rep Performance:** Incentivize top-performing sales reps and address underperformance for a motivated and effective sales team.
- **Geographic Expansion:** Make informed decisions on expanding or optimizing market presence in profitable regions.
- **Cost Management:** Optimize freight costs relative to product costs for improved overall cost management.
- **Yearly Performance Comparison:** Facilitate strategic planning and goal-setting through year-to-year performance comparison.
- **Customer-Centric Approach:** Tailor products and services based on customer preferences for enhanced satisfaction and loyalty.

