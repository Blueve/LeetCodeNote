Customers Who Never Order
==========

## C++


```sql
SELECT Name as Customers
FROM Customers
WHERE Id NOT IN (SELECT CustomerId FROM Orders);
```
