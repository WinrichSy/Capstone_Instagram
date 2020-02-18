<p align="center"><img src="Pictures/instacart-vector-logo.png"></p>
# **Instacart 2017 Trend Analysis**  

## Description  
A deep dive into the Paris AirBnb dataset to get a better understanding on successful hosts on AirBnb. What is needed to gain Superhost status based on various attributes and predict if hosts are on their way to gain that status. 

## Table of Contents
[1. Background & Motivation](#Background&Motivation)<br>
[2. Null Hypothesis](#NullHypothesis)<br>
[3. Data Source](#DataSource)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3a. About The Data](#data)<br>
[4. Exploratory Data Analysis](#EDA)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4a. Orders Made by Instacart Users During 2017](#3a)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4b. Users Ordering Stats](#3b)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4c. Timeframe of Orders](#3c)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4d. Most Ordered Items in 2017](#3d)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4e. Products Based on Departments](#3e)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4f. Number of Organic vs Non Organic Products](#3f)<br>
[5. P-Test Hypothesis](#Hypothesis)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[5a. P-Testing](#4a)<br>
[6. Conclusions](#Conclusions)<br>
[7. Future Plans](#FuturePlans)<br>
[8. Dependencies](#Dependencies)<br>
[9. Contact](#Contact)<br>

## <a id="Background&Motivation">Background & Motivation</a>
What is Instacart?
Instacart is a same-day grocery delivery and pick-up service in the U.S. and Canada founded in 2012. Customers shop for groceries through their app and or website and have their groceries delivered or ready for pick-up at local groceries. They are partnered with major grocery chains such as Costco, ALDI, Sam's Club, Sprouts, and etc. Concurrently serve more than 20,000 different grocery stores across more than 5,500 cities in North America.

Instacart's customers choose what groceries they want and add them into their digital cart online and or cell phone app. Instacart's personal shoppers pick, pack and deliver the order within the customer's designated time frame. For orders of $35 or more, the delivery fee is $3.99. With an Instacart Express membership for $9.99/month or an annual fee of $99, customers get unlimited, free delivery on orders over $35.

Why Instacart?
Instacart has been used to save customers trips to and from the groceries and time from searching for their products within the stores. With its growing popularity, its useful to understand what items are being bought and at what rate. That information can be used to help retainers to know what to stock up on. 

---
## <a id="NullHypothesis">Null Hypothesis</a>
Null_Hypothesis: Instacart users prefer ordering non-organic products instead of organic products.  
Alt_Hypothesis: Instacart users DO prefer ordering ORGANIC products over non-organic products.  
alpha: 0.05  

---
## <a id="DataSource">DataSource</a>
Dataset can be downloaded at: https://www.instacart.com/datasets/grocery-shopping-2017  

### <a id="data">3a. About the Data</a>
aisles.csv (134 rows, 2 columns):  
Attritubes:  
 |-- aisle_id: integer (nullable = true) aisle identifier  
 |-- aisle: string (nullable = true) the name of the aisle  

departments.csv (21 rows, 2 columns):  
Attributes:  
 |-- department_id: integer (nullable = true) department identifier  
 |-- department: string (nullable = true) the name of the department  

order_products_prior.csv (32434489 rows, 4 columns):  
Attributes:  
 |-- order_id: integer (nullable = true) foreign key  
 |-- product_id: integer (nullable = true) foreign key  
 |-- add_to_cart_order: integer (nullable = true) order in which each product was added to cart  
 |-- reordered: integer (nullable = true) 1 if product has been ordered by this user in the past, 0 otherwise  

orders.csv (3421083 rows, 7 columns):  
Attributes:  
 |-- order_id: integer (nullable = true) order identifier  
 |-- user_id: integer (nullable = true) customer identifier  
 |-- eval_set: string (nullable = true) which evaluation set this order belongs in  
 |-- order_number: integer (nullable = true) the order sequence number for this user (1=first, n=nth)  
 |-- order_dow: integer (nullable = true) the day of the week the order was placed on  
 |-- order_hour_of_day: integer (nullable = true) the hour of the day the order was placed on  
 |-- days_since_prior_order: double (nullable = true) days since the last order, capped at 30  

products.csv (49688  rows, 4 columns):
Attributes:  
 |-- product_id: integer (nullable = true) product identifier  
 |-- product_name: string (nullable = true) name of the product  
 |-- aisle_id: string (nullable = true) foreign key  
 |-- department_id: string (nullable = true) foreign key  
 
---
# <a id="EDA">Exploratory Data Analysis</a>
## <a id="4a">4a. Orders Made by Instacart Users During 2017</a>
95481 Instacart users placed at most 10 orders within 2017. There is also 1990 users that have placed orders at least 90 times throught the year. 
<p align="center"><img src="Orders Made by Instacart Users During 2017.png"></p>

## <a id="4b">4b. Users Ordering Stats</a>
1,836,581 Instacart orders had at most 10 items placed. Whereas 36 orders had at least 90 products.
<p align="center"><img src="Graphs/13. Number of Items Bought per Order.png"></p>

When it comes to users adding products into their cart, bananas have the highest priority. Other itmes added into a cart first is primarily food. 
<p align="center"><img src="Graphs/12. Graphs/8. Top 12 Products Added First in Carts.png"></p>

## <a id="4c">4c. Timeframe of Orders</a>
Most Instacart users do their shopping on the weekend. There is a 25% increase in ordering activity during Saturday and Sunday compared to the other days of the week. 
<p align="center"><img src="Graphs/15. Orders Placed During Day of Week.png"></p>

Instacart users barely do their shopping at 3AM. Only 5474 orders were placed at 3AM within 2017. Whereas the time that most users are active shopping is at 10AM, with 288,418 orders being placed within 2017.
<p align="center"><img src="Graphs/14. Number of Orders During Time of Day.png"></p>

This is a breakdown on the number of orders placed based on day of the week.
<p align="center"><img src="Graphs/16. Number of Orders During Time of Day.png"></p>

When separated into weekdays vs weekends, there are a huge differents in orders made during the week.
<p align="center"><img src="Graphs/17. Number of Orders During Time of Day.png"></p>

## <a id="4d">4d. Most Ordered Items in 2017</a>
Out of all the items ordered through Instacart in 2017, Bananas are the most prevalent item ordered.
<p align="center"><img src="Graphs/1. 12 Most Ordered Items in 2017.png"></p>

## <a id="4e">4e. Products Based on Departments</a>
Although produces are ordered the most, there are four times more personal care products available for ordering. 
<p align="center"><img src="Graphs/2.Available products per dept.png"></p>

The number of items ordered based on department are not linear with the amount of products the department have available. Althought there are 6562 unique personal care products, those items were ordered 447123 times. Whereas produces were ordred 9,479,291 times with only 1684 unique produces are available.
<p align="center"><img src="Graphs/3. Total Numbers of Orders based on Dept.png"></p>

In terms of percentage, produces were 29.23% of all orders placed through Instacart during 2017. Dairy and eggs made up 16.69% of all orders within Instacart during 2017.
<p align="center"><img src="Graphs/4. Percentage of orders by dept.png"></p>

Bananas are the most popular item within the produce department. Organic Whole Milk from the dairy/eggs department were ordered 137905 times.
<p align="center"><img src="Graphs/5. Most Popular Item Per Department.png"></p>

## <a id="4f">4f. Organic vs Non Organic Products</a>
Number of non-organic products is remarkably higher than organic products available. There are only 5035 organic products compared to the 44653 non-organic products available.
<p align="center"><img src="Graphs/9. Number of Organic vs Non Organic.png"></p>

Looking solely at milk/eggs and produce department, the total number of organic products available make up 31.60% of all produces available. 
<p align="center"><img src="Graphs/11. Percentages of Organic vs Non Organic.png"></p>

The top 12 most popular organic items include bag of organic bananas and organic strawberries.
<p align="center"><img src="Graphs/6. 12 Most Popular Organic Products.png"></p>

The top 12 most popular non organic items includes bananas and large strawberries as well.
<p align="center"><img src="Graphs/7. 12 Most Popular Non Organic Products.png"></p>

These are the number of organic vs non-organic items that were barely ordered during 2017. Meaning each item were ordered less than 10 times throughout the year.
<p align="center"><img src="Graphs/10. Amount of Unpopular Organic vs Non Organic Products.png"></p>


---
## <a id="Hypothesis">P-Test</a>
Low p-test value means we reject the null hypothesis that people prefer non-organic products over organic products.

---
## <a id="Conclusions">Conclusions</a>
In conclusion, people ordering through Instacart prefer organic products over non-organic products!

---
## <a id="FuturePlans">Future Plans</a>
If these attributes were available:  
1. retailer_id {name of grocery}: Show how which grocery was prominently used in Instacart  
2. purchase_date {date an order was made}:  
     a. Show time plot of what items were ordered and if food trends influenced specific orders. Then graph them along google time plot of specific searches. Like kale and matcha.  
     b. What type of products were ordered during the seasons: Winter, Spring, Summer, and Fall  
     c. What were the typical orders during the start of the year and how they change over time. New Year, new me mentality.  
3. to_customer_time_date {time and date customers put to pick up or get delivered}: Show preffered time customers like their delivery  
4. delivery_pick_up {string regarding customers' perferred method of getting grocery, pick up or delivered}: Show which method of getting grocery is more preferred.  
5. order_price {total price of order in float type}: Show average amount customers pay for their grocery and how often it goes above the $35 limit for cheaper shipping.  
6. user_start {date when user created an instacart account}: Can be used to determine the average amount of orders per week. 

---
## <a id="Dependencies">Dependencies</a> 

---
## <a id="Contact">Contact</a>
Feel free to contact me about any questions. I can be reached through these links.  
[LinkedIn](https://www.linkedin.com/in/winrichsy/)  
[Email](winrichsy@gmail.com)  
