# SQL Commands

## Useful commands

```sql
	> show all -- Display all variable

	> set sqlprompt 'prompt name'
	> set linesize 100
	> set pagesize 100

	> clear screen
	> @ 'path/to/script.sql' -- Execute scripts

	DESC table; -- Display table attributes
	SELECT sysdate FROM dual; -- Get date format

```

## All `SELECT` commands

### Basics

```sql	
	SELECT * FROM table;
  	SELECT column FROM table;
  	SELECT DISTINCT column FROM table; -- DISTINCT or UNIQUE
  	
```

### `WHERE` keyword - conditions

* Basic conditions

```sql
	SELECT column FROM table WHERE column='value'; -- Text Field
	SELECT column FROM table WHERE column>50; -- Numeric

	-- Multiple conditions
	SELECT * FROM table
	WHERE column!=30
	AND (column<=40 OR NOT column>=40);

```

* `IN` condition

```sql
	SELECT * FROM table
	WHERE column IN ('a','b','c');

	SELECT * FROM table1
	WHERE column IN (SELECT column FROM table2); -- Subquery: more below
```

*  `BEWTWEEN` condition

```sql
	SELECT * FROM table
	WHERE column BETWEEN 50 AND 90;

	SELECT * FROM table
	WHERE column
	BETWEEN #07/04/2018# AND #09/05/2018#; -- Between dates
```

* `LIKE` condition (`CHAR` datatype only)

```sql
	SELECT * FROM table
	WHERE column LIKE 'a%'; -- Starts with a
					  '%a'; -- Ends with a
					  '%a%'; -- a in any position
					  '_a%'; -- a in second position
					  'a%b'; -- Starts with a ends with b

```

* `NULL` values

```sql
	SELECT * FROM table WHERE column IS NULL;
	SELECT * FROM table WHERE column IS NOT NULL;
```


### `ORDER BY` keyword - sort

* Single column

```sql
	SELECT * FROM table ORDER BY column; -- Default ascending
	SELECT * FROM table ORDER BY column DESC; -- Descending
```

* Multiple columns

```sql
	SELECT * FROM table ORDER BY column1, column2;
	SELECT * FROM table ORDER BY column1 DESC, column2 ASC;
```

### `GROUP BY` keyword - count duplicates

* Display and group column duplicated value

```sql
	SELECT COUNT(*) FROM table GROUP BY column;
	-- works with (COUNT, MAX, MIN, AVG, SUM)
```

* Use `HAVING` keyword for condition

```sql
	SELECT SUM(column) AS new_column_name -- alias
	FROM table 
	GROUP BY column
	HAVING SUM(column)>1;
	
```


### Multiple tables

* Joining 2 tables

```sql
  	SELECT * FROM table1, table2 
  	WHERE table1.column=table2.column
```

* Joining columns from different tables

```sql
  	SELECT table1.column, table2.column 
  	FROM table1, table2 
  	WHERE column=column;

  	-- 2 tables 1 conditiion, 3 tables 2 condition and so on
  	SELECT table1.column, table2.column, table3.column
  	FROM table1, table2, table3 
  	WHERE table1.column=table2.column 
  	AND table2.column=table2.column;
```


### `UPDATE` and `DELETE` keywords

* Update table column values

```sql 
	UPDATE table SET column='value' WHERE column='value';
```

* Delete table column values

```sql
	DELETE FROM table WHERE column='value';
```

* Renaming table

```sql
	RENAME tableold TO table new;
```

### `TO_CHAR` 

* Use for date formatting

```sql
	SELECT TO_CHAR(sysdate, 'YYYY') AS "Current Year" FROM dual;
```

* Can be used for condition

```sql
	SELECT column
	FROM table
	WHERE TO_CHAR(date, 'YYYY')=2018;
```

### Subquery

* Query inside a query

```sql
	SELECT column FROM table WHERE column
	IN (SELECT column FROM table WHERE column='value');
```




## Creating a table 

```sql
	CREATE TABLE myfirsttable(
		firstname char(15) NOT NULL,
		last_name char(20) NOT NULL
	);
```






