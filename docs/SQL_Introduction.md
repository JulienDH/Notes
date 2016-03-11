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
