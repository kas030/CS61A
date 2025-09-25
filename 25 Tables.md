# Tables

## Joining Tables

In order to consider multiple tables, we have to include something called a join.

Tables A & B are joined by a comma (or `JOIN`) to form all combos of a row from A & a row from B.

### Joining Two Tables

Continue the dog breeder example before:

```sql
CREATE TABLE dogs AS
  SELECT "ace" AS name, "long" AS fur UNION
  SELECT "bella"      , "short"       UNION
  SELECT "charlie"    , "long"        UNION
  SELECT "daisy"      , "long"        UNION
  SELECT "ellie"      , "short"       UNION
  SELECT "finn"       , "curly"       UNION
  SELECT "ginger"     , "short"       UNION
  SELECT "hank"       , "curly";
```

@import "img/tables-01.png" {width=360}

Select the names of the parents of curly-furred dogs:

```sql
SELECT parent FROM parents, dogs
              WHERE child = name AND fur = "curly";
```

The statement `SELECT * FROM parents, dogs` will create a table consisting of all the pairs of rows from parents and dogs.

### Implicit & Explicit Join Syntax

A join typically has some conditions for matching up the rows of two (or more) tables.

- Implicit syntax: Use a comma (or just `JOIN`) and put all conditions in the `WHERE` clause (like the example above).
- Explicit syntax: Use `FROM __ JOIN __ ON __` and put matching conditions after `ON`.

Rewrite the query above using explicit syntax:

```sql
SELECT parent FROM parents JOIN dogs ON child = name
              WHERE fur = "curly";
```

## Aliases and Dot Expressions

If two tables have the same column name, then we need a dot expression to distinguish which column we are talking about.

If two tables have the same name, then we need an alias to distinguish them.

These both occur when we join a table with itself.

### Joining a Table with Itself

Two tables may share a column name; dot expressions and aliases disambiguate column values.

```sql
SELECT [column] FROM [table] WHERE [condition] ORDER BY [order];
```

`[table]` is a comma-separated list of table names with **optional aliases**.

Select all pairs of siblings:

```sql
SELECT a.child AS first, b.child AS second
  FROM parents AS a, parents AS b
  WHERE a.parent = b.parent AND a.child < b.child;
```

@import "img/tables-02.png" {width=320}

### Joining Multiple Tables

Multiple tables can be joined to yield all combinations of rows from each.

```sql
CREATE TABLE grandparents AS
  SELECT a.parent AS grandog, b.child AS granpup
    FROM parents AS a, parents AS b
    WHERE b.parent = a.child
```

Select all grandparents with the same fur as their grandchildren:

```sql
SELECT grandog FROM grandparents, dogs AS c, dogs as d
               WHERE grandog = c.name AND
                     granpup = d.name AND
                     c.fur = d.fur;
```

## Numerical Expressions

Expressions can contain **function calls** and **arithmetic operators**, which can occur in any expression within a select statement.

- Combine values: `+`, `-`, `*`, `/`, `%`, `and`, `or`
- Transform values: `abs`, `round`, `not`, `-`
- Compare values: `<`, ,`<=`, `>`, `>=`, `<>`, `!=`, `=`

## String Expressions

String values can be combines to form longer strings through the **concatenation operator**:

```bash
sqlite> SELECT "hello," || " world";
hello, world
```

Basic string manipulation is built into SQL:

```sql
CREATE TABLE phrase AS
  SELECT "hello," || " world" as s;
SELECT substr(s, 4, 2) || substr(s, instr(s, " ") + 1, 1) FROM phrase;
```

The statements above will get the string `low` as the result.

Strings can be used to represent structured values, but doing so is rarely a good idea:

```sql
CREATE TABLE lists AS
  SELECT "one" AS car, "two,three,four" AS cdr;
SELECT substr(cdr, 1, instr(cdr, ",") - 1) AS cadr FROM lists;
```
