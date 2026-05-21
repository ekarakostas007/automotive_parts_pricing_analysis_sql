# Automotive Parts Pricing Analysis (SQL)

## Overview

This project demonstrates SQL database design and analytical querying using a sanitized automotive parts pricing dataset.  The database simulates customer-specific part information and pricing data commonly used in manufacturing and operations environments.

The goal of this project is to demonstrate practical SQL skills including table creation, relationships, filtering, joins, views, aggregation, and business-oriented analysis.

---

## Project Objectives

- Build a relational database structure
- Create relationships using primary and foreign keys
- Store customer and part information
- Analyze customer-specific pricing data
- Practice common SQL operations used in business environments

---

## Database Structure

### Customers Table

Stores customer information:

| Column | Data Type |
|----------|-----------|
| customer_id | SERIAL |
| customer_name | VARCHAR |

### Piston Rings Table

Stores part-level information:

| Column | Data Type |
|----------|-----------|
| part_id | SERIAL |
| customer_id | INT |
| customer_part_number | VARCHAR |
| tpr_part_number | VARCHAR |
| model | VARCHAR |
| description | TEXT |
| price_2026 | NUMERIC |

---

## SQL Concepts Demonstrated

- CREATE TABLE
- PRIMARY KEY
- FOREIGN KEY
- INSERT INTO
- CREATE VIEW
- INNER JOIN
- WHERE
- LIKE
- ORDER BY
- GROUP BY
- COUNT
- AVG
- ROUND
- Filtering and conditional logic
- Data aggregation

---

## Example Business Questions Answered

### How many parts does each customer have?

```sql
SELECT
    c.customer_name,
    COUNT(p.part_id) AS total_parts
FROM customers c
JOIN piston_rings p
ON c.customer_id = p.customer_id
GROUP BY c.customer_name;
```

### What is the average part price by customer?

```sql
SELECT
    c.customer_name,
    ROUND(AVG(p.price_2026),4) AS average_price_2026
FROM customers c
JOIN piston_rings p
ON c.customer_id = p.customer_id
GROUP BY c.customer_name;
```

### Which parts have the highest prices?

```sql
SELECT *
FROM piston_rings_view
ORDER BY price_2026 DESC;
```

---

## Technologies Used

- PostgreSQL
- SQL
- pgAdmin

---

## Notes

This project uses sanitized sample data for portfolio purposes only and does not contain real customer, pricing, or proprietary business information.

## Author

Developed by Eva Karakostas  

M.S. Data Science | Operations Supervisor | Data Analytics | Process Automation
