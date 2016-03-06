Combine Two Tables
==========

## C++


```sql
SELECT FirstName, LastName, City, State
FROM Person
LEFT JOIN Address ON Person.PersonId = Address.PersonId;
```
