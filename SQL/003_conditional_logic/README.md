<!-- HEADER -->
<div align="center">
  <h1 align="center">3. Conditional Logic</h1>
</div>

# Usage
```shell
SELECT first_name, last_name,
  CASE
    WHEN active = 1 THEN 'ACTIVE'
    ELSE 'INACTIVE'
  END activity_type ## customize the column name
FROM customer;
```
> CASE (switch) - END / WHEN (if) - ELSE
> 
```shell
SELECT CASE
  WHEN condition1 THEN result1
    CASE
      WHEN condition2 THEN result2
      WHEN condition3 THEN result3
      ELSE result4
    END
  ELSE result5
FROM table
```

