# SQL basic commands

## SQL SELECT Statement

The SELECT statement is used to select data from a database.
The result is stored in a result table, called the result-set.

```
SELECT column_name,column_name
FROM table_name;
```
and
```
SELECT * FROM table_name;
```

## SQL SELECT DISTINCT Statement

The SELECT DISTINCT statement is used to return only different values contain in column.

## SQL WHERE Clause

The WHERE clause is used to filter records.
```
SELECT column_name,column_name
FROM table_name
WHERE column_name operator value;
```
SQL requires single quotes around text values. However, numeric fields should not be enclosed in quotes.

## SQL AND & OR Operators

The AND & OR operators are used to filter records based on more than one condition.
```
SELECT * FROM Customers
WHERE Country='Germany'
AND City='Berlin';
```
It's possible to combine AND and OR (use parenthesis to form complex expressions).
```
SELECT * FROM Customers
WHERE Country='Germany'
AND (City='Berlin' OR City='München');
```

## SQL ORDER BY Keyword

The ORDER BY keyword is used to sort the result-set by one or more columns.
The result is in ascending order by default. To sort the records in a descending order, you can use the DESC keyword.
```
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

## SQL INSERT INTO Statement

The INSERT INTO statement is used to insert new records in a table.
```
INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);
```

## SQL UPDATE Statement

The UPDATE statement is used to update records in a table.
```
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;
```

## SQL Injection

An SQL Injection can destroy your database.
The only proven way to protect a web site from SQL injection attacks, is to use SQL parameters.

##  SQL SELECT TOP Clause

The SELECT TOP clause is used to specify the number of records to return.
```
SELECT TOP number|percent column_name(s)
FROM table_name;
```

## SQL LIKE Operator

The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.
```
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;
```

## SQL Wildcards

In SQL, wildcard characters are used with the SQL LIKE operator. SQL wildcards are used to search for data within a table.
|Wildcard|Description|
|---|---|
|%|A substitute for zero or more characters|
|_|A substitute for a single character|
|[charlist]|Sets and ranges of characters to match|
|[^charlist]|Matches only a character NOT specified within the brackets|
|[!charlist]|Matches only a character NOT specified within the brackets|
