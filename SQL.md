# QA-Lead-Assessment-Rubini Part 4: SQL Knowledge Test
**1.Retrieve all users who have placedmore than 5 orders**
Assuming we have two tables users(with user_id) and orders(with user_id that references users)

SELECT u.*
FROM users u
JOIN(
    SELECT user_id
    FROM orders
    GROUP BY user_id
    HAVING COUNT(*) > 5
    ) o ON u.user_id = o.user_id;

**2.Join tables to get order details with customer information**
Assuming users table has fields like user_id,name,email,etc and orders table has fields like order_id,user_id,order_date,total_amount etc
SQL query is given below to retrieves each order along with the corresponding user's name,email and ID.
SELECT
  o.order_id,
  o.order_date,
  o.total_amount,
  u.user_id,
  u.name,
  u.email
FROM orders o
JOIN users u ON o.user_id = u.user_id;


