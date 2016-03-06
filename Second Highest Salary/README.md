Second Highest Salary
==========

## C++


```sql
SELECT MAX(B.Salary)
FROM Employee AS A
LEFT JOIN Employee AS B ON A.Salary > B.Salary;
```
Better
```sql
SELECT MAX(Salary)
FROM Employee
WHERE Salary < (SELECT MAX(Salary) FROM Employee);
```
Better
```sql
SELECT IF(COUNT(*) = 0, NULL, RES.Salary)
FROM
    (SELECT Salary
    FROM Employee
    GROUP BY Salary
    ORDER BY Salary DESC
    LIMIT 1,1) AS RES;
```
