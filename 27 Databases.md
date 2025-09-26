# Databases

## Create Table and Drop Table

### Create Table

`CREATE TABLE` expression syntax:

@import "img/databases-01.png" {width=600}

`column-def`:

@import "img/databases-02.png" {width=550}

`table-options`:

@import "img/databases-03.png" {width=260}

Examples:

```sql
CREATE TABLE numbers (n, note);
CREATE TABLE numbers (n UNIQUE, note);
CREATE TABLE numbers (n, note DEFAULT "No comment");
```

## Drop Table

`DROP TABLE` expression syntax:

@import "img/databases-04.png" {width=680}

If we run drop table on a name that doesn't exists without `IF EXISTS` clause,
we will reach an error.

## Modifying Tables

### Insert

@import "img/databases-05.png" {width=500}

For a table `t` with two columns...

- To inset into one column:  
`INSERT INTO t(column) VALUES (value);`
- To insert into both columns:  
`INSERT INTO ty VALUES (value0, value1);`

If we want to insert more rows then we can follow these parentheses by comma and more parenthetical row descriptions.

### Update

@import "img/databases-06.png" {width=500}

Update sets all entries in certain columns to new values, just for some subset of rows.

The common usage of `UPDATE` statement:

```sql
UPDATE t SET c1 = v1, c2 = v2, ... WHERE ...;
```

### Delete

@import "img/databases-07.png" {width=500}

`DELETE` remove some or all rows from a table.
