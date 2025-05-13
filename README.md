# Week8Assignment
answers.sql
SELECT checkNumber, paymentDate, amount
FROM payments;
-- Get order dates, required dates, and status for 'In Process' orders
-- Sorted by order date (newest first)
SELECT orderDate, requiredDate, status
FROM orders
WHERE status = 'In Process'
ORDER BY orderDate DESC;

-- Get first name, last name, and email of Sales Reps
-- Ordered by employee number (highest first)
SELECT firstName, lastName, email
FROM employees
WHERE jobTitle = 'Sales Rep'
ORDER BY employeeNumber DESC;


-- Get complete office information
SELECT *
FROM offices;

-- Get product names and stock quantities
-- Sorted by buy price (cheapest first), limited to 5 records
SELECT productName, quantityInStock
FROM products
ORDER BY buyPrice ASC
LIMIT 5;


