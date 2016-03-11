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
|:---------:|-----------|
|     %     |A substitute for zero or more characters|
|     _     |A substitute for a single character|
|[charlist] |Sets and ranges of characters to match|
|[^charlist]|Matches only a character NOT specified within the brackets|
|[!charlist]|Matches only a character NOT specified within the brackets|


The following SQL statement selects all customers with a City ending with the letter "s":
```
SELECT * FROM Customers
WHERE City LIKE 's%';
```
The following SQL statement selects all customers with a City ending with the letter "s":
```
SELECT * FROM Customers
WHERE City LIKE '%s';
```
The following SQL statement selects all customers with a Country containing the pattern "land":
```
SELECT * FROM Customers
WHERE Country LIKE '%land%';
```
The following SQL statement selects all customers with a City starting with any character, followed by "erlin":
```
SELECT * FROM Customers
WHERE City LIKE '_erlin';
```
The following SQL statement selects all customers with a City starting with "L", followed by any character, followed by "n", followed by any character, followed by "on":
```
SELECT * FROM Customers
WHERE City LIKE 'L_n_on';
```
The following SQL statement selects all customers with a City starting with "b", "s", or "p":
```
SELECT * FROM Customers
WHERE City LIKE '[bsp]%';
```
The following SQL statement selects all customers with a City NOT starting with "b", "s", or "p":
```
SELECT * FROM Customers
WHERE City LIKE '[!bsp]%';

or

SELECT * FROM Customers
WHERE City NOT LIKE '[bsp]%';
```

## SQL IN Operator

The IN operator allows you to specify multiple values in a WHERE clause.
```
SELECT * FROM Customers
WHERE City IN ('Paris','London');
```

## SQL BETWEEN Operator

The BETWEEN operator selects values within a range. The values can be numbers, text, or dates.
```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
The following SQL statement selects all products with a price BETWEEN 10 and 20, but products with a CategoryID of 1,2, or 3 should not be displayed:
```
SELECT * FROM Products
WHERE (Price BETWEEN 10 AND 20)
AND NOT CategoryID IN (1,2,3);
```
The following SQL statement selects all orders with an OrderDate BETWEEN '04-July-1996' and '09-July-1996':
```
SELECT * FROM Orders
WHERE OrderDate BETWEEN #07/04/1996# AND #07/09/1996#;
```

## SQL Aliases

SQL aliases are used to give a database table, or a column in a table, a temporary name. Basically aliases are created to make column names more readable.
```
SELECT column_name AS alias_name
FROM table_name;

or

SELECT column_name(s)
FROM table_name AS alias_name;
```
In the following SQL statement we combine four columns (Address, City, PostalCode, and Country) and create an alias named "Address":
```
SELECT CustomerName, Address+', '+City+', '+PostalCode+', '+Country AS Address
FROM Customers;
```

## SQL Joins

An SQL JOIN clause is used to combine rows from two or more tables, based on a common field between them.

### INNER JOIN

The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns in both tables.
```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name=table2.column_name;
```
