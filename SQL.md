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
🔹 a. Schema Validation
Ensure that all tables, columns, data types, constraints, and indexes are correctly defined.

Tools: Liquibase, Flyway, SQL scripts for schema comparisons.

🔹 b. Data Accuracy
Insert known data and verify it is correctly stored and retrievable.

Check for correct calculations, formatting, and default values.

🔹 c. Referential Integrity
Ensure child records cannot exist without valid parent records.

Test deletion/update cascades where defined.

Try inserting invalid foreign keys — ensure failure is handled properly.

🔹 d. Uniqueness Constraints
Attempt to insert duplicate data in fields that require uniqueness.

Verify that duplicates are rejected appropriately.

🔹 e. Not Null Constraints
Attempt to insert NULL in columns where it’s not allowed.

Ensure appropriate error handling or default values.

🔹 f. Transaction Consistency
Test atomic operations: commit, rollback, and savepoint functionality.

Example: If one part of a transaction fails, the entire operation should roll back.

🔹 g. Data Migration and ETL Validation
When migrating data, validate that all records are accurately transferred.

Compare source and target counts, and sample content.

🔹 h. Stored Procedure / Trigger Testing
Test triggers fire correctly under intended conditions.

Validate outputs, side effects, and rollback scenarios.

3. Tools for Database Testing
SQL scripts – Manual or automated test queries.

DBUnit / JDBC / JPA – For integration with Java-based apps.

Postman + Newman – For testing APIs that interact with the DB.

Flyway / Liquibase – For version control and schema testing.

Data Factory / Faker – For generating synthetic test data.

4. Automation Integration
Integrate database integrity tests into your CI/CD pipeline to run:

After code deployment

After DB schema updates

During nightly regression builds

5. Example Test Case
Test Case: Ensure referential integrity for Orders and Customers tables

Precondition: Orders table has a foreign key to Customers.

Test: Try inserting an order with a non-existent customer_id.

Expected Result: DB should reject the insert with a foreign key constraint error.

**Best Practices**
1. Use a clean test DB or mock DB for each run.

2. Seed with known data for consistent results.

3. Ensure rollback or teardown after each test to maintain state.

4. Validate boundary and edge cases like long strings, nulls, special characters.

