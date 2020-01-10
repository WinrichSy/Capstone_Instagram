Instacart 2017 Trend Analysis

What is Instacart?
Instacart is a same-day grocery delivery and pick-up service in the U.S. and Canada founded in 2012. Customers shop for groceries through their app and or website and have their groceries delivered or ready for pick-up at local groceries. They are partnered with major grocery chains such as Costco, ALDI, Sam's Club, Sprouts, and etc. Concurrently serve more than 20,000 different grocery stores across more than 5,500 cities in North America.

Instacart's customers choose what groceries they want and add them into their digital cart online and or cell phone app. Instacart's personal shoppers pick, pack and deliver the order within the customer's designated time frame. For orders of $35 or more, the delivery fee is $3.99. With an Instacart Express membership for $9.99/month or an annual fee of $99, customers get unlimited, free delivery on orders over $35.

Why Instacart?
Instacart has been used to save customers trips to and from the groceries and time from searching for their products within the stores. With its growing popularity, its useful to understand what items are being bought and at what rate. That information can be used to help retainers to know what to stock up on. 

Dataset can be downloaded at: https://www.instacart.com/datasets/grocery-shopping-2017  

The csvs in dataset folder and their schema:  
aisles.csv rows:  134  
root  
 |-- aisle_id: integer (nullable = true) aisle identifier  
 |-- aisle: string (nullable = true) the name of the aisle  

departments.csv rows:  21  
root  
 |-- department_id: integer (nullable = true) department identifier  
 |-- department: string (nullable = true) the name of the department  

order_products_prior.csv rows:  32434489  
root  
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

NOTES:
1. order_products_train.csv is not used. It contains generated information from Instacart used for testing purposes only. Does not represent actual information obtained from orders.
2. No retailerID, grocery stores' id, are not included in the datasets
3. Unfortunately, date of purchases are not included in these datasets
4. Product info doesn't include prices of the items
5. Orders doesn't include total price paid


Future Plans  
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
