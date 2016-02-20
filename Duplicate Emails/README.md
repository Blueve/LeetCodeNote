Duplicate Emails
==========

## C++

  - Answer

  ```sql
  SELECT A.Email FROM Person as A
  JOIN Person as B ON B.Id != A.Id AND B.Email = A.Email
  GROUP BY A.Email;
  ```

  ```sql
  SELECT Email FROM Person
  GROUP BY Email
  HAVING count(*) > 1;
  ```