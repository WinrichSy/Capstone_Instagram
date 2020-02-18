# **Instacart 2017 Trend Analysis**  
<p align="center"><img src="Pictures/instacart-vector-logo.png"></p>
## Description  
A deep dive into the Paris AirBnb dataset to get a better understanding on successful hosts on AirBnb. What is needed to gain Superhost status based on various attributes and predict if hosts are on their way to gain that status. 

## Table of Contents
[1. Background & Motivation](#Background&Motivation)<br>
[2. Data Source](#DataSource)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2a. About The Data](#data)<br>
[3. Exploratory Data Analysis](#EDA)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3a. Most Ordered Items in 2017](#3a)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3b. Available Products Per Department](#3b)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3c. Total Number of Orders Based on Department](#3c)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3d. Percentage of Orders by Department](#3d)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3e. Organic vs Non Organic Products](#3e)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3f. Orders Made by Instacart Users During 2017](#3f)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3h. Top 12 Products Added First Into Carts](#3h)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3i. Number of Items Bought per Order](#3i)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3j. Number of Orders Placed During Time of Day](#3j)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3k. Orders Placed During Day of Week](#3k)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[3l. Number of Orders During Time of Day](#3l)<br>
[4. P-Test Hypothesis](#Hypothesis)<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[4a. P-Testing](#4a)<br>
[5. Conclusions](#Conclusions)<br>
[6. Future Plans](#FuturePlans)<br>
[7. Dependencies](#Dependencies)<br>
[8. Contact](#Contact)<br>

## <a id="Background&Motivation">Background & Motivation</a>
What is Instacart?
Instacart is a same-day grocery delivery and pick-up service in the U.S. and Canada founded in 2012. Customers shop for groceries through their app and or website and have their groceries delivered or ready for pick-up at local groceries. They are partnered with major grocery chains such as Costco, ALDI, Sam's Club, Sprouts, and etc. Concurrently serve more than 20,000 different grocery stores across more than 5,500 cities in North America.

Instacart's customers choose what groceries they want and add them into their digital cart online and or cell phone app. Instacart's personal shoppers pick, pack and deliver the order within the customer's designated time frame. For orders of $35 or more, the delivery fee is $3.99. With an Instacart Express membership for $9.99/month or an annual fee of $99, customers get unlimited, free delivery on orders over $35.

Why Instacart?
Instacart has been used to save customers trips to and from the groceries and time from searching for their products within the stores. With its growing popularity, its useful to understand what items are being bought and at what rate. That information can be used to help retainers to know what to stock up on. 

---
## <a id="DataSource">DataSource</a>
Dataset can be downloaded at: https://www.instacart.com/datasets/grocery-shopping-2017  

### <a id="data">2a. About the Data</a>
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

orders.csv rows:  3421083  
root  
 |-- order_id: integer (nullable = true) order identifier  
 |-- user_id: integer (nullable = true) customer identifier  
 |-- eval_set: string (nullable = true) which evaluation set this order belongs in  
 |-- order_number: integer (nullable = true) the order sequence number for this user (1=first, n=nth)  
 |-- order_dow: integer (nullable = true) the day of the week the order was placed on  
 |-- order_hour_of_day: integer (nullable = true) the hour of the day the order was placed on  
 |-- days_since_prior_order: double (nullable = true) days since the last order, capped at 30  

products.csv rows:  49688  
root  
 |-- product_id: integer (nullable = true) product identifier  
 |-- product_name: string (nullable = true) name of the product  
 |-- aisle_id: string (nullable = true) foreign key  
 |-- department_id: string (nullable = true) foreign key  
 
---
## <a id="EDA">Exploratory Data Analysis</a>
### <a id="3a">3a. Most Ordered Items in 2017</a>

<p align="center"><img src="Graphs/1. 12 Most Ordered Items in 2017.png"></p>

### <a id="3b">3b. Available Products Per Department</a>

<p align="center"><img src="Graphs/2.Available products per dept.png"></p>

### <a id="3c">3c. Total Number of Orders Based on Department</a>

<p align="center"><img src="Graphs/3. Total Numbers of Orders based on Dept.png"></p>

### <a id="3d">3d. Percentage of Orders by Department</a>

<p align="center"><img src="Graphs/4. Percentage of orders by dept.png"></p>

<p align="center"><img src="Graphs/5. Most Popular Item Per Department.png"></p>

### <a id="3e">3e. Organic vs Non Organic Products</a>

<p align="center"><img src="Graphs/9. Number of Organic vs Non Organic.png"></p>
<p align="center"><img src="Graphs/11. Percentages of Organic vs Non Organic.png"></p>
<p align="center"><img src="Graphs/6. 12 Most Popular Organic Products.png"></p>
<p align="center"><img src="Graphs/7. 12 Most Popular Non Organic Products.png"></p>
<p align="center"><img src="Graphs/10. Amount of Unpopular Organic vs Non Organic Products.png"></p>

### <a id="3f">3f. Orders Made by Instacart Users During 2017</a>

<p align="center"><img src="AirBnb Capstone Graphs/5. Hist - Hosts vs Superhosts.png"></p>


### <a id="3h">3h. Top 12 Products Added First Into Carts</a>

<p align="center"><img src="Graphs/12. Orders Made by Instacart Users During 2017.png"></p>

### <a id="3i">3i. Number of Items Bought per Order</a>

<p align="center"><img src="Graphs/13. Number of Items Bought per Order.png"></p>

### <a id="3j">3j. Timeframe of Orders</a>

<p align="center"><img src="Graphs/14. Number of Orders During Time of Day.png"></p>
<p align="center"><img src="Graphs/15. Orders Placed During Day of Week.png"></p>
<p align="center"><img src="Graphs/16. Number of Orders During Time of Day.png"></p>
<p align="center"><img src="Graphs/17. Number of Orders During Time of Day.png"></p>
---
## <a id="Hypothesis">P-Test</a>
### <a id="4a">4a. Models WITH Verification Dummies</a>

<p align="center"><img src="AirBnb Capstone Graphs/6.1 ROC curve w verification dummies.png"></p>

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
