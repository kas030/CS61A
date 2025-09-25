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

The clause `SELECT * FROM parents, dogs` will create a table consisting of all the pairs of rows from parents and dogs.

### Implicit & Explicit Join Syntax

A join typically has some conditions for matching up the rows of two (or more) tables.

- Implicit syntax: Use a comma (or just `JOIN`) and put all conditions in the `WHERE` clause (like the example above).
- Explicit syntax: Use `FROM __ JOIN __ ON __` and put matching conditions after `ON`.

Rewrite the query above using explicit syntax:

```sql
SELECT parent FROM parents JOIN dogs ON child = name
    WHERE fur = "curly";
```
