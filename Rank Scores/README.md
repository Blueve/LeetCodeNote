Rank Scores
==========

## C++


```sql
SELECT 
    Score, 
    (SELECT COUNT(DISTINCT Score) 
     FROM Scores 
     WHERE Scores.Score >= s.Score) AS Rank
FROM Scores AS s
ORDER BY Score DESC
```
Better
```sql
SELECT 
    Score, 
    (SELECT COUNT(*) 
     FROM (SELECT DISTINCT Score AS S
           FROM Scores) AS Tmp
     WHERE S >= Score) AS Rank
FROM Scores
ORDER BY Score DESC
```
