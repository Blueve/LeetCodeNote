Consecutive Numbers
==========

## C++


```sql
SELECT DISTINCT l1.Num
FROM Logs AS l1, Logs AS l2, Logs AS l3
WHERE l1.Id + 1 = l2.Id AND l2.Id + 1 = l3.Id AND l1.Num = l2.Num AND l2.Num = l3.Num
```
