# SQL

## Databases

Database management systems (DBMS):

A table is a collection of records, which are rows that have a value for each column.

The Structured Query Language (SQL) is perhaps the most widely used programming language.

SQL is a **declarative programming language**.

### Declarative Programming

In **declarative languages** such as SQL & Prolog:

- A "program" is a description of the desired result.
- The interpreter figures out how to generate the result.

In **imperative language** such as Python & Scheme:
- A "program" is a description of computational processes.
- The interpreter carries out execution/evaluation rules.

An example of an SQL query:

```sql
SELECT "West Coast" AS region, name FROM cities
  WHERE longitude >= 115
  ORDER BY latitude;
```

@import "img/sql-01.png" {width=280}

The role of a query is to take an existing table, like the cities table above, and **build another table**.

In this case,
we'll create one that has "West Coast" as one of the values in each row,
along with the name of the city.

@import "img/sql-02.png" {width=190}

## Structured Query Language

### Selecting Value Literals

A `SELECT` statement always includes a comma-separated list of column descriptions.

A **column description** is an expression, optionally followed by `AS` and a column name:

```sql
SELECT [expressions] AS [name], [expression] AS [name], ...;
```

Selecting literals creates a one-row table.

The union of two select statements is a table containing the rows of both of their results.

```sql
SELECT "daisy" AS parent, "hank" AS child UNION
SELECT "ace"            , "bella"         UNION
SELECT "ace"            , "charlie"       UNION
SELECT "finn"           , "ace"           UNION
SELECT "finn"           , "dixie"         UNION
SELECT "finn"           , "ginger"        UNION
SELECT "ellie"          , "finn";
```

Notice that when we union together a bunch of select statements, we get no guarantees about the order of the result. That's up to the declarative programming engine, which tries to compute the results efficiently.

### Naming Tables

The result of a `SELECT` statement is displayed to the user, but not stored.

A `CREATE TABLE` statement gives the result of a `SELECT` statement a name:

```sql
CREATE TABLE [name] AS [select statement];
```

So we can give the table we created before a name like this:

```sql
CREATE TABLE parents AS
  SELECT "daisy" AS parent, "hank" AS child UNION
  SELECT "ace"            , "bella"         UNION
  SELECT "ace"            , "charlie"       UNION
  SELECT "finn"           , "ace"           UNION
  SELECT "finn"           , "dixie"         UNION
  SELECT "finn"           , "ginger"        UNION
  SELECT "ellie"          , "finn";
```

@import "img/sql-03.png" {width=320}

## Projecting Tables

### Select Statements Project Existing Tables

- A `SELECT` statement can specify an input table using a `FROM` clause.
- A subset of the rows of the input table can be selected using a `WHERE` clause.
- An ordering over the remaining rows can be declared using an `ORDERED BY` clause.

```sql
SELECT [columns] FROM [table] WHERE [condition] ORDERED BY [order];
```

- Column descriptions determine how each input row is projected to a result row:

```sql
[expressions] AS [name], [expression] AS [name], ...
```

## Arithmetic

### Arithmetic in Select Expressions

In a select expression, column names evaluates to row values.

Arithmetic expressions can combine row values and constants.

```sql
CREATE TABLE lift AS
  SELECT 101 AS chair, 2 as single, 2 as couple UNION
  SELECT 102         , 0          , 3           UNION
  SELECT 103         , 4,         , 1;

SELECT chair, single + 2 * couple AS total FROM lift;
```

@import "img/sql-04.png" {width=270}
