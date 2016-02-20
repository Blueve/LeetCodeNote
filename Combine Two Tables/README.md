Combine Two Tables
==========

## C++

  - Answer

  ```sql
  SELECT FirstName, LastName, City, State
  FROM Person
  LEFT JOIN Address ON Person.PersonId = Address.PersonId;
  ```