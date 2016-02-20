Customers Who Never Order
==========

## C++

  - Answer

  ```sql
  SELECT Name as Customers
  FROM Customers
  WHERE Id NOT IN (SELECT CustomerId FROM Orders);
  ```