---
title: MySQL Basics
date: 2025-03-12 17:25:13
categories:
- MySQL
tags:
---

# 1 Querying data

## 1.1 SELECT

```sql
SELECT select_list
FROM table_name;
```

<img src="/images/mysql-select-from.png" >

## 1.2 ORDER BY

```sql
SELECT 
   select_list
FROM 
   table_name
ORDER BY 
   column1 [ASC|DESC], 
   column2 [ASC|DESC],
   ...;
```

To use `union` and `order by` together.

* remove the first `order by`

```sql

```

* Sort the two query result sets separately using `ORDER BY`.

```sql
SELECT * FROM
(SELECT * FROM t1 WHERE username LIKE 'l%' ORDER BY score ASC) t3
UNION
SELECT * FROM
(SELECT * FROM t1 WHERE username LIKE '%m%' ORDER BY score ASC) t4
```
