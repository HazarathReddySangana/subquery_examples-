# subquery_examples-


# Subqueries and Nested Queries in SQL

## 📌 Overview

This project demonstrates how to use **subqueries** and **nested queries** in SQL for advanced data retrieval.
I created a sample database with two tables:

* **Customers** → Stores customer details.
* **Orders** → Stores order details linked to customers.

The project covers **different types of subqueries** such as scalar subqueries, `IN`, `EXISTS`, and correlated subqueries.

---

## 🎯 Objectives

* Learn to write subqueries in **SELECT, WHERE, and FROM** clauses.
* Understand **scalar** and **correlated** subqueries.
* Use subqueries with **IN, EXISTS, =** operators.
* Build **advanced query logic** for real-world scenarios.

---

## 🛠 Tools Used

* **MySQL Workbench** (you can also use SQLite DB Browser)
* SQL language

---

## 📂 Database Structure

### Customers Table

| Column Name  | Type        | Description          |
| ------------ | ----------- | -------------------- |
| CustomerID   | INT (PK)    | Unique customer ID   |
| CustomerName | VARCHAR(50) | Customer's full name |
| Country      | VARCHAR(50) | Customer’s country   |

### Orders Table

| Column Name | Type          | Description               |
| ----------- | ------------- | ------------------------- |
| OrderID     | INT (PK)      | Unique order ID           |
| CustomerID  | INT (FK)      | Linked to Customers table |
| Amount      | DECIMAL(10,2) | Order amount              |
| OrderDate   | DATE          | Date of order             |

---

## 📊 Sample Data

Customers:

| CustomerID | CustomerName | Country |
| ---------- | ------------ | ------- |
| 1          | John Smith   | USA     |
| 2          | Priya Sharma | India   |
| 3          | Ahmed Khan   | UAE     |
| 4          | Li Wei       | China   |

Orders:

| OrderID | CustomerID | Amount  | OrderDate  |
| ------- | ---------- | ------- | ---------- |
| 101     | 1          | 2000.00 | 2025-08-01 |
| 102     | 2          | 5000.00 | 2025-08-02 |
| 103     | 3          | 1500.00 | 2025-08-03 |
| 104     | 1          | 3000.00 | 2025-08-04 |
| 105     | 4          | 2500.00 | 2025-08-05 |

---

## 📌 Example Queries

### 1. Scalar Subquery

Find customers with orders greater than the average order amount.

```sql
SELECT CustomerName, Country
FROM Customers
WHERE CustomerID IN (
    SELECT CustomerID
    FROM Orders
    WHERE Amount > (SELECT AVG(Amount) FROM Orders)
);
```

### 2. IN Subquery

Find customers who placed at least one order.

```sql
SELECT CustomerName
FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Orders);
```

### 3. EXISTS Subquery

Find customers who have at least one order.

```sql
SELECT CustomerName
FROM Customers c
WHERE EXISTS (
    SELECT 1
    FROM Orders o
    WHERE o.CustomerID = c.CustomerID
);
```

### 4. Correlated Subquery

Find orders greater than the average order amount of that customer.

```sql
SELECT OrderID, CustomerID, Amount
FROM Orders o
WHERE Amount > (
    SELECT AVG(Amount)
    FROM Orders
    WHERE CustomerID = o.CustomerID
);
```

---

## ✅ Outcomes

* Learned how to use **scalar, correlated, IN, and EXISTS** subqueries.
* Practiced **nested query logic** for real-world database operations.
* Understood how subqueries improve **data analysis and filtering** in SQL.

---

## 📷 Suggested Output Screenshots

When submitting, add screenshots of:

1. Tables (`SELECT * FROM Customers;`, `SELECT * FROM Orders;`)
2. Query results for each subquery.
