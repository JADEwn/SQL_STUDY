# SQL_Leetcode_**183. Customers Who Never Order**

## [Problem]

Link (https://leetcode.com/problems/customers-who-never-order/)

---

![Untitled](%E1%84%8E%E1%85%A2%E1%84%8C%E1%85%A2%E1%84%89%E1%85%A5%E1%86%AB(5%2030)%209575fcc89f2d4b93b2c13e05fb2343f7/Untitled.png)

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

![Untitled](%E1%84%8E%E1%85%A2%E1%84%8C%E1%85%A2%E1%84%89%E1%85%A5%E1%86%AB(5%2030)%209575fcc89f2d4b93b2c13e05fb2343f7/Untitled%201.png)

## 다른 사람 풀이

---

```python
SELECT name as Customers
FROM Customers
WHERE id NOT IN (SELECT **distinct** customerId FROM Orders)
```
