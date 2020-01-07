Instacart 2017 Trend Analysis

Note: Dataset is too large to update to Github.
Dataset can be downloaded at: https://www.instacart.com/datasets/grocery-shopping-2017

The csvs in dataset folder and their schema
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

Project History:
Jan 6, 2020 - Took the dataset from instacart's website for analysis. Decided on using Spark SQL for querying and filtering what content I need for visualization. Figuring out my pipeline process to avoid bottlenecks with some of the databases that hold 32 million rows. Had some trouble with SQL query and delve deeper into nested subqueries. Have 2 bar graphs up, but need to modify it to make them more presentable/readable.

Todo: Update graphs to show different colors based on products' department and have a legend for them.

Jan 7, 2020 -

Todo: Group the lowest 10 departments and have it as its own section. Compare it to the other departments and all their items combined.
