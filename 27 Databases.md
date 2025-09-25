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
