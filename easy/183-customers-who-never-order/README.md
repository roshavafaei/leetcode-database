# 183. Customers Who Never Order 🛒

## Problem

We are given two tables:

### Customers

| Column Name | Type |
|-------------|------|
| id | int |
| name | varchar |

### Orders

| Column Name | Type |
|-------------|------|
| id | int |
| customerId | int |

Write a query to find all customers who have never placed an order.

The result should contain the customer names under the column name `Customers`.

---

## Approach 💡

We use a `LEFT JOIN` because we want to keep every row from the `Customers` table.

The two tables are connected using:

Customers.id = Orders.customerId

If a customer has never placed an order, there will be no matching row in the `Orders` table.

In that case, the columns from `Orders` will be `NULL`.

So we filter the result using:

o.id IS NULL

---

## Solution ✅

SELECT c.name AS Customers
FROM Customers c
LEFT JOIN Orders o
    ON c.id = o.customerId
WHERE o.id IS NULL;

---

## Why LEFT JOIN?

`LEFT JOIN` keeps all customers, even if they do not have a matching order.

If we used `INNER JOIN`, customers without orders would disappear from the result.

By checking:

o.id IS NULL

we keep only the customers who have no matching order.

---

## Key Concept 🔑

The important relationship is:

Customers.id = Orders.customerId

`Customers.id` identifies the customer.

`Orders.customerId` tells us which customer placed each order.

---

## What I Learned 📚

- How to use `LEFT JOIN` to find missing relationships
- Why `Customers.id` should be matched with `Orders.customerId`
- How `IS NULL` is used to find rows without a match
- Why `= NULL` does not work in SQL
- How aliases like `c` and `o` make queries shorter and easier to read
