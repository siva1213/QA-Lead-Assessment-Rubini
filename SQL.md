# QA-Lead-Assessment-Rubini Part 4: SQL Knowledge Test
**1.Retrieve all users who have placedmore than 5 orders**<br>
Assuming we have two tables users(with user_id) and orders(with user_id that references users)<br>

SELECT u.* <br>
FROM users u <br>
JOIN( <br>
    SELECT user_id <br>
    FROM orders <br>
    GROUP BY user_id <br>
    HAVING COUNT(*) > 5 <br>
    ) o ON u.user_id = o.user_id; <br>

**2.Join tables to get order details with customer information**<br>
Assuming users table has fields like user_id,name,email,etc and orders table has fields like order_id,user_id,order_date,total_amount etc
SQL query is given below to retrieves each order along with the corresponding user's name,email and ID.
SELECT<br>
  o.order_id,<br>
  o.order_date,<br>
  o.total_amount,<br>
  u.user_id,<br>
  u.name,<br>
  u.email<br>
FROM orders o<br>
JOIN users u ON o.user_id = u.user_id;<br>


