# Index
- [Index](#index)
- [DML (Table changing)](#dml-table-changing)
  - [UPDATE Statement](#update-statement)
  - [INSERT Statement](#insert-statement)
  - [DELETE Statement](#delete-statement)
- [DML (Tables joining)](#dml-tables-joining)
  - [Join using WHERE](#join-using-where)
  - [CROSS JOIN](#cross-join)
  - [INNER JOIN](#inner-join)
  - [OUTER JOIN](#outer-join)
  - [NATURAL JOIN](#natural-join)
- [UNION](#union)
- [Subquery](#subquery)
  - [SELECT with Subquery](#select-with-subquery)
  - [UPDATE with Subquery](#update-with-subquery)
  - [INSERT with Subquery](#insert-with-subquery)
  - [DELETE with Subquery](#delete-with-subquery)
- [DDL](#ddl)
  - [CREATE TABLE](#create-table)
  - [INDEX](#index-1)
  - [VIEW](#view)
- [References](#references)


# DML (Table changing)
## UPDATE Statement

```sql
-- Update all records
UPDATE
    table_name
SET
    column_name = 110
;

-- Update records with condition
UPDATE
    table_name
SET
    column_name = 110
WHERE
    column_name = 108
;
```

## INSERT Statement

```sql
-- Insert with specifying column names
INSERT INTO
    table_name
    (   column1
    ,   column2
    ,   column3
    ) VALUES (
        value1
    ,   value2
    ,   value3
    )
;

-- Insert without specifying
INSERT INTO
    table_name
VALUES (
    value1
,   value2
,   value3
);

-- Insert multiple records
INSERT INTO
    table_name
VALUES
    (1, value1, value2, value3)
,   (2, value1, value2, value3)
,   (3, value1, value2, value3)
;
```

## DELETE Statement

```sql
-- Delete all records
DELETE
FROM
    table_name
;

-- Delete records with condition
DELETE
FROM
    table_name
WHERE
    column_name = 100
;
```

# DML (Tables joining)
## Join using WHERE

```sql
SELECT
    t1.column2
,   t2.column2
FROM
    table_name1 t1
,   table_name2 t2
WHERE
    t1.column1 = t2.column1
```

## CROSS JOIN

```sql
-- Take out all records combinations
SELECT
    t1.column2
,   t2.column2
FROM
    table_name1 t1
CROSS JOIN
    table_name2 t2
```

## INNER JOIN
Only records that match the join condition are extracted.

```sql
SELECT
    t1.column2
,   t2.column2
FROM
    table_name1 t1
INNER JOIN
    table_name2 t2
    ON
        t1.column1 = t2.column1
;
```

## OUTER JOIN
One table is joined as reference to the other.

```sql
SELECT
    t1.column2
,   t2.column2
FROM
    table_name1 t1
LEFT JOIN
    table_name2 t2
    ON
        t1.column1 = t2.column1
;
```

## NATURAL JOIN
Columns of the same name are automatically concatenated.

```sql
SELECT
    t1.column2
,   t2.column2
FROM
    table_name1 t1
NATURAL JOIN
    table_name2 t2
;
```

# UNION

```sql
SELECT
    column_name
FROM
    table_name1
UNION [ALL]
SELECT
    column_name
FROM
    table_name2
;
```

- `UNION ALL` does not remove duplicates.
- `INTERSECT`: Intersect
- `EXCEPT (or MINUS)`: Set difference

# Subquery
## SELECT with Subquery

```sql
SELECT
    column_name
FROM
    table_name
SELECT
    column_name IN (
        SELECT
            column
        FROM
            table
        WHERE
            column = 100
    )
;
-- Commonly used operators for subqueries
---- IN, NOT IN, EXISTS, NOT EXISTS etc.
```

## UPDATE with Subquery

```sql
UPDATE
    table_name
SET
    column_name1 = (
        SELECT
            MAX(column)
        FROM
            table
    )
WHERE
    column_name2 = 100
;
```

## INSERT with Subquery

```sql
INSERT INTO
    table_name
VALUES (
    (SELECT MAX(column) + 1 FROM table)
,   value2
,   value3
);
```

## DELETE with Subquery

```sql
DELETE
FROM
    table_name
WHERE
    column_name = (
        SELECT
            MIN(column)
        FROM
            table
    )
;
```

# DDL
## CREATE TABLE

```sql
-- PRIMARY KEY, NOT NULL, UNIQUE
CREATE TABLE
    table_name
    (
        column1 NUMERIC(8) PRIMARY KEY
    ,   column2 DATE NOT NULL
    ,   column3 VARCHAR(10) UNIQUE
    ,   column4 NUMERIC(4)
    )
;

-- Composite PRIMARY KEY, FOREIGN KEY
CREATE TABLE
    table_name
    (
        column1 NUMERIC(8)
    ,   column2 DATE NOT NULL
    ,   column3 VARCHAR(10) UNIQUE
    ,   column4 NUMERIC(4)
    ,   PRIMARY KEY(column1, column2)
    ,   FOREIGN KEY(column4)
            REFERENCES other_table(columnA)
    )
;
```

What is the CONSTRAINT phrase???

## INDEX

```sql
-- Create index
CREATE INDEX
    index_name
    ON
        table_name(column_name)
;

-- Delete index
DROP INDEX
    index_name
;
```

## VIEW

```sql
-- Create view
CREATE VIEW
    view_name
    AS (
        SELECT
            column1, column2
        FROM
            table_name
        WHERE
            column3 = 100
    )
;
```

# References
[SQLスタイルガイド - Qiita](https://qiita.com/taise/items/18c14d9b01a5dfd6d35e)
