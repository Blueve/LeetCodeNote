Rising Temperature
==========

## C++

  - Answer

  ```sql
  SELECT A.Id
  FROM Weather as A
  LEFT JOIN Weather as B ON DATEDIFF(A.Date, B.Date) = 1
  WHERE A.Temperature > B.Temperature;
  ```