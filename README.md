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
 |-- aisle_id: integer (nullable = true)  
 |-- aisle: string (nullable = true)  

departments.csv rows:  21  
root  
 |-- department_id: integer (nullable = true)  
 |-- department: string (nullable = true)  

order_products_prior.csv rows:  32434489  
root  
 |-- order_id: integer (nullable = true)  
 |-- product_id: integer (nullable = true)  
 |-- add_to_cart_order: integer (nullable = true)  
 |-- reordered: integer (nullable = true)  

orders.csv rows:  3421083  
root  
 |-- order_id: integer (nullable = true)  
 |-- user_id: integer (nullable = true)  
 |-- eval_set: string (nullable = true)  
 |-- order_number: integer (nullable = true)  
 |-- order_dow: integer (nullable = true)  
 |-- order_hour_of_day: integer (nullable = true)  
 |-- days_since_prior_order: double (nullable = true)  

products.csv rows:  49688  
root  
 |-- product_id: integer (nullable = true)  
 |-- product_name: string (nullable = true)  
 |-- aisle_id: string (nullable = true)  
 |-- department_id: string (nullable = true)  

NOTES:
1. order_products_train.csv is not used. It contains generated information from Instacart used for testing purposes only. Does not represent actual information obtained from orders.
2. No retainerID, grocery stores' id, are not included in the datasets
3. Unfortunately, date of purchases are not included in these datasets
4. Product info doesn't include prices of the items
5. Orders doesn't include total price paid


