Employees Earning More Than Their Managers
==========

## C++


```sql
SELECT A.Name as Employee FROM Employee as A
LEFT JOIN Employee as B on B.Id = A.ManagerId
WHERE A.Salary > B.Salary;
```
