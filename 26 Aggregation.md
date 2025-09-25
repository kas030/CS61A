# Aggregation

## Aggregate Functions

We can perform aggregation over multiple rows using aggregate functions.

An aggregate function in the `[columns]` clause computes a value from a **group of rows**.

Here's a table of animals:

```sql
CREATE TABLE animals AS
  SELECT "dog" AS kind, 4 AS legs, 20 AS weight UNION
  SELECT "cat"        , 4        , 10           UNION
  SELECT "ferret"     , 4        , 10           UNION
  SELECT "parrot"     , 2        , 6            UNION
  SELECT "penguin"    , 2        , 10           UNION
  SELECT "t-rex"      , 2        , 12000;
```

@import "img/aggregation-01.png" {width=310}

```sql
SELECT max(legs) from animals;
```

@import "img/aggregation-02.png" {width=103}

More examples:

```bash
sqlite> select avg(legs) from animals;
3.0
sqlite> select count(legs) from animals;
6
sqlite> select count(kind) from animals;
6
sqlite> select count(*) from animals;
6
sqlite> select count(distinct legs) from animals;
2
sqlite> select sum(distinct weight) from animals;
12036
```

### Mix Aggregate Functions and Single Values

An aggregate function also selects a row in the table, which may be meaningful:

```bash
>sqlite select max(weight), kind from animals;
12000|t-rex
```

Notice that if there are more than one things that have the maximum value, the answer will be ambiguous.

Some aggregations don't give us meaningful values, like `avg`:

```bash
sqlite> select avg(weight) from animals;
2009.33333333333|t-rex
```

## Groups

By default, all rows that are used to compute the final table,
meaning the ones that passed the filter in the where clause,
are all in the same group.
And so the result of an aggregate function only has one row.

### Grouping Rows

Rows in a table can be grouped, and aggregation is **performed on each group** individually.

```sql
SELECT [columns] FROM [table] GROUP BY [expression] HAVING [expression];
```

The number of groups is the number of unique values of the expression placed after the `GROUP BY` clause.

```sql
SELECT legs, max(weight) FROM animals GROUP BY legs;
```

@import "img/aggregation-03.png" {width=700}

A `HAVING` clause filters the set of groups that are aggregated:

```sql
SELECT weight / legs, count(*) FROM animals
  GROUP BY weight / legs
  HAVING count(*) > 1;
```

@import "img/aggregation-04.png" {width=230}
