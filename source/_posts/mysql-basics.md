---
title: mysql-basics
date: 2025-03-12 17:25:13
categories:
- MySQL
tags:
---



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
