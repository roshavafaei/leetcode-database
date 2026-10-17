# 175. Combine Two Tables 🧩

## Problem

Given two tables:

### Person

| Column Name | Type |
|-------------|------|
| personId | int |
| lastName | varchar |
| firstName | varchar |

### Address

| Column Name | Type |
|-------------|------|
| addressId | int |
| personId | int |
| city | varchar |
| state | varchar |

Write a query to return the `firstName`, `lastName`, `city`, and `state` of each person.

If a person does not have a matching address, `city` and `state` should be returned as `NULL`.

---

## Approach 💡

We use a `LEFT JOIN` because we want to keep every row from the `Person` table, even if there is no matching row in the `Address` table.

The two tables are connected using:

Person.personId = Address.personId

If there is no matching address, the columns from the `Address` table will automatically be returned as `NULL`.

---

## Solution ✅

SELECT
    p.firstName,
    p.lastName,
    a.city,
    a.state
FROM Person p
LEFT JOIN Address a
    ON p.personId = a.personId;

---

## Why LEFT JOIN?

`LEFT JOIN` returns:

- All rows from the left table (`Person`)
- Matching rows from the right table (`Address`)
- `NULL` values when no match exists in the right table

If we used `INNER JOIN`, people without an address would not appear in the result.

---

## Key Concept 🔑

`LEFT JOIN` = all rows from the left table + matching rows from the right table.

---

## What I Learned 📚

- How to combine data from two tables
- The difference between `INNER JOIN` and `LEFT JOIN`
- How `NULL` values appear when no matching row exists
- How table aliases like `p` and `a` make SQL queries cleaner
