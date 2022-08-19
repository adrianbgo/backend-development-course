# Week 7: Intro to SQL


## SQL Syntax
__Summary__: SQL is a declarative language, therefor its syntax will read like a natural language. SQL statements will begin with a verb which 
describes the action, for example [SELECT](#select), [INSERT](#insert), [UPDATE](#update), or [DELETE](#delete). After the verb will come the 
subject, and finally the predicate.

The predicate will specify all conditions for the query.

See the following:
```sql
SELECT
    first_name
FROM
    employees
WHERE
    YEAR(birth_date) = 1993;
```

As you can see, it reads just like English.

Get the first names of all employees born in 1993.

### SQL Commands

SQL has a nearly infinite number of commands. Each SQL command is usually terminated with a semicolon (;). For example, the following are 2 
SQL commands separated by a semicolon.

```sql
SELECT
    first_name, last_name
FROM
    employees;

DELETE FROM employees
WHERE
    hire_date < '1990-01-01'
```

Each SQL command is composed of a variety of tokens that can be literals, keywords, identifiers, or expressions. These tokens are usually separated
by space, tabs, or newlines.

#### Literals

Literals are explicit values which are referred to in other languages as constants. SQL provides 3 "flavors" of literals: string, numeric, and binary.

String literals are one or more alphanumeric characters surrounded by single quotes.

```sql
'Adrian'
'1996-08-22'
'25'
```

Note how 25 is a number and 1996-08-22 is a date. However, when you surround them in single quotes, SQL will interpret them as a string literal.

Generally, SQL tends to be *case sensitive* with respect to literals, so the value `'Adrian'` is not the same as `'ADRIAN'`.

Numeric literals are the integer, decimal, or scientific notation.

```sql
200
-5
6.0221415E23
```

SQL represents binary values using the notation `x'0000'`, where each digit is a [hexadecimal](#hexadecimal) value.

```sql
x'01'
x'0f0ff'
```

#### Keywords

SQl has numerous keywords which each have special meanings, such as [SELECT](#SELECT), [INSERT](#INSERT), [UPDATE](#UPDATE), [DELETE](#DELETE), and 
[DROP](#DROP). These are the reserved words, therefore you can't use them as the names of columns, tables, views, indexes, stored procedures,
triggers, or any other database object.

#### Identifiers

Identifiers refer to specific objects in the database (e.g., tables, columns, indexes, etc.). SQL is case-insensitive with respect
to keywords and identifiers.

The following would be equivalent.

```sql
Select * From employees;
SELECT * FROM EMPLOYEES;
select * from employees;
SELECT * FROM employees;
```

For the sake of readability, SQL keywords will generally be UPPERCASE and identifiers in lowercase throughout the cheat sheet.

#### Comments

To document your SQL statements, you may use SQL comments. When parsing SQL statements with comments, the database engine will ignore 
the characters inside of the comments.

Comments are denoted by two consecutive hyphens (`--`) that allow you to comment the rest of the line.

```sql
SELECT
    employee_id, salary
FROM
    employees
WHERE
    salary < 3000; -- employees with a low salary
```

This is an SQL comment.

```sql
-- employees with low salary
```

To document the code that can span multiple lines, you can also use multiline notation (`/**/`).

```sql
/* increase 5% for employees who make less than 3,000
   no other employees will be affected. */
UPDATE employees
SET
    salary = salary * 1.05
WHERE
    salary < 3000;
```

## Some Useful SQL Commands

### SELECT

```sql 
SELECT * 
FROM table_name 
WHERE condition=true
```

### UPDATE

```sql
UPDATE table_name
SET column_name_1 = new_value,
    column_name_2 = new_value
WHERE condition = true;
```

### INSERT

```sql
INSERT INTO table_name(column_list)
VALUES(value_list),
	(value_list);
```

### DELETE

```sql
DELETE FROM table_name 
WHERE condition=true;
```

### DROP

```sql
DROP TABLE table_name;
/* Don't do this unless you know what you're doing. This will delete the entire table from the database. */
```

## Some Useful Tips

### Binary, Decimal, and Hexadecimal Conversions

| __Binary__ | __Decimal__ | __Hexadecimal__ |
|--|--|--|
| 0 | 0 | 0 |
| 1 | 1 | 1 |
| 10 | 2 | 2 |
| 11 | 3 | 3 |
| 100 | 4 | 4 |
| 101 | 5 | 5 |
| 110 | 6 | 6 |
| 111 | 7 | 7 |
| 1000 | 8 | 8 |
| 1001 | 9 | 9 |
| 1010 | 10 | a |
| 1011 | 11 | b |
| 1100 | 12 | c |
| 1101 | 13 | d |
| 1110 | 14 | e |
| 1111 | 15 | f |
| 10000 | 16 | 10 |


