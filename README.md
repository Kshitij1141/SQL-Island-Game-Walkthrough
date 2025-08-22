# SQL-Island-Game-Walkthrough
![Tool](https://img.shields.io/badge/Tool-SQL-lightgreen?style=flat-square) 
![Platform](https://img.shields.io/badge/Platform-MySQL%20%7C%20PostgreSQL-blue?style=flat-square)
![Concepts](https://img.shields.io/badge/Concepts-SELECT%20%7C%20WHERE%20%7C%20JOIN-orange?style=flat-square)
![Advanced](https://img.shields.io/badge/Advanced-UPDATE%20%7C%20INSERT%20%7C%20DELETE-purple?style=flat-square)
![Project](https://img.shields.io/badge/Project-SQL%20Island%20Game-brightblue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

This guide provides a complete, step-by-step walkthrough of the SQL Island game, with every query and a detailed explanation of the SQL concepts used.

---

# 🗺️ SQL Island Adventure Guide

Welcome to the SQL Island Adventure!  
Follow the journey of **Kshitij** through the island as you learn SQL basics step-by-step. Each chapter introduces queries with detailed explanations designed for beginners.

---

## Table of Contents

- [About This Guide](#about-this-guide)  
- [Key SQL Concepts](#key-sql-concepts)  
- [Database Schema](#database-schema-your-data-blueprint)  
- [Chapter 1: The Crash](#chapter-1-the-crash)  
- [Chapter 2: The Treasure Hunt](#chapter-2-the-treasure-hunt)  
- [Chapter 3: The Job Market](#chapter-3-the-job-market)  
- [Chapter 4: The Rescue Mission](#chapter-4-the-rescue-mission)  
- [Chapter 5: The Final Showdown](#chapter-5-the-final-showdown)  

---

## About This Guide

This guide is designed for **beginners** learning SQL through a fun island adventure story. Every query is explained clearly so you can understand **why** and **how** it works.

---

## Key SQL Concepts

| Keyword      | Purpose                                           | Simple Explanation                                      |
|--------------|---------------------------------------------------|---------------------------------------------------------|
| `SELECT`     | Retrieve data from tables                         | "Show me these columns or everything."                  |
| `FROM`       | Specify the table to retrieve data from           | "Look in this table for the data."                      |
| `WHERE`      | Filter rows based on conditions                   | "Only show rows that meet this condition."              |
| `AND`        | Combine multiple filter conditions                | "Rows must meet all these conditions."                  |
| `LIKE`       | Search text patterns                              | "Find text that matches this pattern."                  |
| `IN`         | Check if value is in a list of values             | "Match any of these options."                           |
| `UPDATE`     | Modify existing data                              | "Change data in the table."                             |
| `INSERT INTO`| Add new rows                                      | "Add new data to the table."                            |
| `DELETE`     | Remove rows permanently                           | "Delete rows from the table."                           |
| `JOIN`       | Combine rows from two tables                      | "Link tables based on related columns."                 |

---

## Database Schema: Your Data Blueprint

| Table          | Columns                                                           | Description                          |
|----------------|-------------------------------------------------------------------|--------------------------------------|
| **INHABITANT** | `personid` (INT), `name` (VARCHAR), `villageid` (INT),            | Details of all island inhabitants    |
|                | `job` (VARCHAR), `gold` (INT), `state` (VARCHAR)                  |                                      |
|                |                                                                   |                                      |
| **VILLAGE**    | `villageid` (INT), `name` (VARCHAR), `chief` (INT)                | Villages and their chiefs            |
|                |                                                                   |                                      |
| **ITEM**       | `itemid` (INT), `item` (VARCHAR), `owner` (INT)                   | Items owned or found by inhabitants  |

---
## Chapter 1: The Crash

You crash on SQL Island and meet the locals.
---

### ❓ Q1: See all inhabitants
```sql
SELECT *
FROM INHABITANT;
```

#### 💡 What it does:
This query selects every row and every column from the `INHABITANT` table.

👉 **In beginner-friendly terms:**  
It shows you a **complete list of all the people living on the island**.

---
### ❓ Q2: Find the butcher

```sql
SELECT *
FROM INHABITANT
WHERE job = 'butcher';
```

#### 💡 What it does:
This query looks in the `INHABITANT` table and returns the row(s) where the `job` is `'butcher'`.

👉 **In beginner-friendly terms:**  
It finds the **person whose job is butcher**.

---
### ❓ Q3: Find Stranger

```sql
SELECT personid
FROM INHABITANT
WHERE name = 'Stranger';
```

#### 💡 What it does:
This query looks inside the `INHABITANT` table and finds the row where the `name` is `'Stranger'`.  
It then returns the `personid` of that inhabitant.

👉 **In beginner-friendly terms:**  
It tells you the **ID number of the person called Stranger**.

---
### ❓ Q4: Find any kind of smith

```sql
SELECT * FROM INHABITANT 
WHERE job LIKE '%smith' 
  AND state = 'friendly';
```

#### 💡 What it does:
This query searches the `INHABITANT` table and returns all columns for inhabitants whose job ends with `'smith'` (e.g., blacksmith, goldsmith, silversmith) **and** whose state is `'friendly'`.

👉 **In beginner-friendly terms:**  
It finds **friendly people who work as some kind of smith**.

---
## Chapter 2: The Treasure Hunt
---
### ❓ Q5: Find your person ID

```sql
SELECT personid 
FROM INHABITANT 
WHERE name = 'Stranger';
```

#### 💡 What it does:
This query searches the `INHABITANT` table and returns the `personid` of the inhabitant named `'Stranger'`. It filters the rows to find the matching name and then only retrieves the `personid` column.

👉 **In beginner-friendly terms:**  
> "Look up the ID of the person named ‘Stranger’."

---
### ❓ Q6: Find ownerless items

```sql
SELECT * FROM ITEM 
WHERE owner IS NULL;
```

#### 💡 What it does:
This query searches the `ITEM` table and returns all rows where the `owner` column has a `NULL` value. `NULL` represents the absence of a value, meaning the items have no owner.

👉 **In beginner-friendly terms:**  
> “Show me all the items that don’t have an owner yet.”

---
### ❓ Q7: Claim all ownerless items

```sql
UPDATE ITEM 
SET owner = 20 
WHERE owner IS NULL;
```

#### 💡 What it does:
This query updates the `ITEM` table by assigning an owner (with `personid = 20`) to all items where the `owner` is `NULL`. The `WHERE owner IS NULL` condition filters for items that currently don’t have an owner, and the `SET owner = 20` assigns the new owner.

👉 **In beginner-friendly terms:**  
> “Claim all the items that don’t have an owner and make them yours!”

---
### ❓ Q8: Find a friendly dealer or merchant

```sql
SELECT * FROM INHABITANT 
WHERE job IN ('dealer', 'merchant') 
  AND state = 'friendly';
```

#### 💡 What it does:
This query searches the `INHABITANT` table and returns all rows where:

- The **`job`** is either `'dealer'` or `'merchant'`,  
- And the **`state`** is `'friendly'`.

It uses the **`IN`** keyword to check for multiple possible job values and combines it with the **`AND`** operator to ensure the person is also friendly.

👉 **In beginner-friendly terms:**  
> “Show me all the friendly people who are either a dealer or a merchant.”

---
### ❓ Q9: Change your name

```sql
UPDATE INHABITANT 
SET name = 'Kshitij' 
WHERE personid = 20;
```

#### 💡 What it does:
This query changes the name of the inhabitant whose `personid` is 20 to `'Kshitij'`. The `WHERE` clause makes sure only that specific person’s name is updated, so no one else is affected.

👉 **In beginner-friendly terms:**  
> “Update your name in the database to ‘Kshitij’.”

---
## Chapter 3: The Job Market
---
### ❓ Q10: Find the richest baker

```sql
SELECT * FROM INHABITANT 
WHERE job = 'baker' 
ORDER BY gold DESC;
```

#### 💡 What it does:  
This query retrieves all inhabitants whose job is 'baker' and sorts them by their gold amount from highest to lowest.

👉 **In beginner-friendly terms:**  
> “Show me all bakers, with the richest baker at the top.”

---

### ❓ Q11: Buy your sword

```sql
UPDATE INHABITANT SET gold = gold + 100 - 150 WHERE personid = 20;
```

#### 💡 What it does:
This query updates the `gold` value for the inhabitant with `personid = 20`. It adds 100 to their current `gold` (representing income or savings) and subtracts 150 (the cost of the sword).

👉 **In beginner-friendly terms:**  
> “Take the current gold, add 100, then subtract 150 to account for buying the sword.”

### ❓ Q12: Get your sword

```sql
INSERT INTO ITEM (item, owner) 
VALUES ('sword', 20);
```

#### 💡 What it does:
This query adds a new row to the `ITEM` table with the item name `'sword'` and assigns the `owner` column to `20`, which corresponds to the `personid` of the inhabitant who will own the sword.

👉 **In beginner-friendly terms:**  
> “We are adding a sword to the list of items and making you (the person with `personid = 20`) its owner.”

### ❓ Q13: Find the kidnapper's village

```sql
SELECT village.name
FROM village, inhabitant
WHERE village.villageid = inhabitant.villageid
  AND inhabitant.name = 'Dirty Dieter';
```

#### 💡 What it does:
This query joins the `village` and `inhabitant` tables on the `villageid` column, allowing us to get the name of the village where `'Dirty Dieter'` lives. The condition `inhabitant.name = 'Dirty Dieter'` filters the results to show only the village of that specific person.

👉 **In beginner-friendly terms:**  
> “Find the village where Dirty Dieter is living by matching the village ID.”

---
## Chapter 4: The Rescue Mission
---

### ❓ Q14: Find the village chief

```sql
SELECT i.name
FROM INHABITANT i
INNER JOIN VILLAGE v ON v.chief = i.personid
WHERE v.name = 'Onionville';
```

#### 💡 What it does:
This query performs an **`INNER JOIN`** between the `INHABITANT` and `VILLAGE` tables. It matches the `chief` column in the `VILLAGE` table with the `personid` in the `INHABITANT` table. By doing this, we retrieve the **name** of the inhabitant who is the chief of the village named `'Onionville'`.

👉 **In beginner-friendly terms:**  
> “Find the name of the person who is the chief of the village called Onionville.”

### ❓ Q15: Defeat the villains

```sql
DELETE FROM INHABITANT 
WHERE name = 'Dirty Dieter';
```
#### 💡 What it does:
This query deletes the row from the `INHABITANT` table where the **`name`** is `'Dirty Dieter'`. It uses the **`DELETE`** command to remove the data. The **`WHERE`** clause ensures that only the villain named `'Dirty Dieter'` is deleted, leaving other inhabitants untouched.

👉 **In beginner-friendly terms:**  
> “Remove the villain named ‘Dirty Dieter’ from the island.”

---
## Chapter 5: The Final Showdown
---

### ❓ Q16: Release the pilot

```sql
UPDATE INHABITANT 
SET state = 'friendly' 
WHERE state = 'kidnapped';
```

#### 💡 What it does:
This query finds all inhabitants whose **`state`** is currently `'kidnapped'` and updates it to `'friendly'`. The **`WHERE`** clause ensures only those with the kidnapped status are updated, so other inhabitants are unaffected.

👉 **In beginner-friendly terms:**  
> “Change the state of the kidnapped person to ‘friendly’ so they’re free.”

### ❓ Q17: Leave the island

```sql
UPDATE INHABITANT 
SET state = 'emigrated' 
WHERE personid = 20;
```

#### 💡 What it does:
This query updates the **`state`** of the inhabitant with **`personid` = 20** to `'emigrated'`. The **`WHERE`** clause ensures that only your row is affected, meaning only your status as an inhabitant is updated.

👉 **In beginner-friendly terms:**  
> “Change my status to ‘emigrated’ because I’ve left the island.”

---

## Conclusion: The End

🎉 Congratulations! You’ve completed all 17 SQL Island challenges.  

By learning how to:  
- Query data (`SELECT`)  
- Filter with conditions (`WHERE`)  
- Use patterns (`LIKE`)  
- Update data (`UPDATE`)  
- Work with ownership and gold  

…you not only rescued yourself but also mastered the core SQL commands needed in real databases.  

👉 **Beginner-friendly takeaway:** SQL is like a treasure map — each query is a clue that helps you discover, filter, and update information.  

🏆 The adventure ends here, but your SQL journey has just begun. The skills you gained on the island will help you explore any new database world.  

**The End.**





