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
SQL query is given below to retrieves each order along with the corresponding user's name,email and ID.<br>
SELECT<br>
  o.order_id,<br>
  o.order_date,<br>
  o.total_amount,<br>
  u.user_id,<br>
  u.name,<br>
  u.email<br>
FROM orders o<br>
JOIN users u ON o.user_id = u.user_id;<br>

**3. Find products with low inventory (less than 10 items)** <br>
Assuming products table has product_id,product_name,etc <br>
and inventory table: product_id,quantity<br>
SQL query<br>
SELECT p.*<br>
FROM products p<br>
JOIN inventory i ON p.product_id = i.product_id<br>
WHERE i.quantity < 10;<br>

**4. Explain your approach to testing database integrity**<br>
Testing database integrity is important to ensure that data is accurate, consistent, and reliable across operations. Here's my approach to testing database integrity:<br>
1. Understand Data Relationships and Constraints
Before testing, gain a clear understanding of:

Primary & Foreign Keys

Unique, Not Null, and Check Constraints

Referential Integrity

Triggers and Stored Procedures

Normalization rules

2. Types of Database Integrity Tests<br>
🔹 a. Schema Validation<br>
Ensure that all tables, columns, data types, constraints, and indexes are correctly defined.<br>

Tools: Liquibase, Flyway, SQL scripts for schema comparisons.<br>

🔹 b. Data Accuracy<br>
Insert known data and verify it is correctly stored and retrievable.<br>

Check for correct calculations, formatting, and default values.<br>

🔹 c. Referential Integrity<br>
Ensure child records cannot exist without valid parent records.<br>

Test deletion/update cascades where defined.<br>

Try inserting invalid foreign keys — ensure failure is handled properly.<br>

🔹 d. Uniqueness Constraints<br>
Attempt to insert duplicate data in fields that require uniqueness.<br>

Verify that duplicates are rejected appropriately.<br>

🔹 e. Not Null Constraints<br>
Attempt to insert NULL in columns where it’s not allowed.<br>

Ensure appropriate error handling or default values.<br>

🔹 f. Transaction Consistency<br>
Test atomic operations: commit, rollback, and savepoint functionality.<br>

Example: If one part of a transaction fails, the entire operation should roll back.<br>

🔹 g. Data Migration and ETL Validation<br>
When migrating data, validate that all records are accurately transferred.<br>

Compare source and target counts, and sample content.<br>

🔹 h. Stored Procedure / Trigger Testing<br>
Test triggers fire correctly under intended conditions.<br>

Validate outputs, side effects, and rollback scenarios.<br>

3. Tools for Database Testing <br>
SQL scripts – Manual or automated test queries.<br>

DBUnit / JDBC / JPA – For integration with Java-based apps.<br>

Postman + Newman – For testing APIs that interact with the DB.<br>

Flyway / Liquibase – For version control and schema testing.<br>

Data Factory / Faker – For generating synthetic test data.<br>

4. Automation Integration <br>
Integrate database integrity tests into your CI/CD pipeline to run:<br>

After code deployment<br>

After DB schema updates<br>

During nightly regression builds<br>

5. Example Test Case <br>
Test Case: Ensure referential integrity for Orders and Customers tables<br>

Precondition: Orders table has a foreign key to Customers.<br>

Test: Try inserting an order with a non-existent customer_id.<br>

Expected Result: DB should reject the insert with a foreign key constraint error.<br>

**Best Practices**
1. Use a clean test DB or mock DB for each run.

2. Seed with known data for consistent results.

3. Ensure rollback or teardown after each test to maintain state.

4. Validate boundary and edge cases like long strings, nulls, special characters.

