Delete Duplicate Emails
==========

## C++

  - Answer

  ```sql
  DELETE FROM Person
  WHERE Id NOT IN (
      SELECT * FROM (
          SELECT MIN(Id)
          FROM Person
          GROUP BY Email) AS TMP
  );
  ```