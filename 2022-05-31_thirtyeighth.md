# SQL_Leetcode_**183. Customers Who Never Order**

## Problem

![image](https://user-images.githubusercontent.com/99947811/171129486-2360391d-edff-4928-9f1b-bc5c7a4cd30a.png)
Link (https://leetcode.com/problems/customers-who-never-order/)


## Solution

---

```sql
SELECT customers.name AS Customers
FROM customers
    LEFT JOIN orders
    ON customers.id = orders.customerId
WHERE orders.id is NULL
```

## Result

---
![image](https://user-images.githubusercontent.com/99947811/171129722-caefe34c-a2fc-44a9-a5f1-0fdcdd5efb39.png)


## 다른 사람 풀이

---

```python
SELECT name as Customers
FROM Customers
WHERE id NOT IN (SELECT **distinct** customerId FROM Orders)
```
