Write a SQL query to report how many units in each category have been ordered on each day of the week. 
Return the result table ordered by category.
![image](https://github.com/Vickey414/SQL-Notes/assets/29950267/2d4dda40-1ed3-4f6d-be4f-5b08af323c57)
![image](https://github.com/Vickey414/SQL-Notes/assets/29950267/e1260436-efa3-4d8a-bf90-748c7030ed97)
```sql
SELECT 
  i.item_category as category,
  sum(case when dayname(o.order_date) = "Monday" then o.quantity else 0) as Monday,
  sum(case when dayname(o.order_date) = "Tuesday" then o.quantity else 0) as Tuesnday,
  sum(case when dayname(o.order_date) = "Wednesday" then o.quantity else 0) as Wednesday,
  sum(case when dayname(o.order_date) = "Thursday" then o.quantity else 0) as Thursday,
  sum(case when dayname(o.order_date) = "Friday" then o.quantity else 0) as Friday,
  sum(case when dayname(o.order_date) = "Saturday" then o.quantity else 0) as Saturday,
  sum(case when dayname(o.order_date) = "Sunday" then o.quantity else 0) as Sunday
FROM items i left join orders o
  ON o.item_id = i.item_id
  GROUP BY i.item_category
ORDER BY i.item_category
```


Write a SQL query to find the most frequently ordered product(s) for each customer. 
The result table should have the product_id and product_name for each customer_id who ordered at least one order.
![image](https://github.com/Vickey414/SQL-Notes/assets/29950267/7370ddf2-e2a3-4a8e-af9d-a2344355ac46)

```sql
SELECT 
c.customer_id, o.product_id, COUNT(*) as 
FROM 
customers c
LEFT JOIN order o 
ON c.customer_id = o.customer_id 
GROUP BY c.customer_id, o.product_id
```

Given the reviews table, write a query to get the average stars for each product every month.
The output should include the month in numerical value, product id, and average star rating rounded to two decimal places.
Sort the output based on month followed by the product id.
<img width="640" alt="image" src="https://github.com/Vickey414/SQL-Notes/assets/29950267/16742811-c405-46e0-89d7-99e11d13bcae">

SELECT 
EXTRACT(MONTH FROM submit_date) AS mth,
product_id, 
ROUND(AVG(stars),2) as avg_stars
FROM 
reviews
GROUP BY EXTRACT(MONTH FROM submit_date), product_id
ORDER BY mth, product_id



