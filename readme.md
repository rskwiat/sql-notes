# SQL Notes

Notes / cheetsheet for remembering SQL commands.

## Creating a Table

```
CREATE TABLE tableName (
  //rows
  name VARCHAR(50),
  data INTEGER
)
```

## Inserting Data

Inside the parens need to be the name of the table columns.

Values 

```
INSERT INTO tableName(name, data)
VALUES('some string', 50);
```

## Primary Keys

Primary Key = Unique id for a record
Foreign Key - ID a record usually in another table that the row is associated with

SERIAL PRIMARY KEY - performance benefits for looking up the ID

```
CREATE TABLE users (
  id SERIAL PRIMAY KEY,
  username VARCHAR(50),
)
```

ID gets created by the `SERIAL PRIMAY KEY`

```
INSERT INTO users(username)
VALUES
  ('test1'),
  ('test2');

```

## Reading Data

Reading all data
```
SELECT * FROM tableName
```

Reading specific rows

```
SELECT name, data FROM tableName
```

## Filtering

Filtering with WHERE keyword

```
SELECT name, FROM tableName where data > 50
```

## Updating Rows

Updating records using WHERE statement finding the row with the name of 'Some String'

```
UPDATE tableName SET data = 500 WHERE name = 'Some string'
```

```
DELETE FROM tableName WHERE name = 'Some String'
```

## Joins

#### Inner Join
Matches only rows that are present.

Joing data from two datbases, `column1` and `columnA` are from two different DBs.

`ex_id` matchs the id found on the `columnA.id`


```
SELECT column1, columnA
FROM table1
JOIN table2 ON columnA.id === table1.ex_id,
```

#### Left Outer Join
Anything that does not match we will not drop it, anything from `table1` without a match will return a value of `null`

```
SELECT column1, columnA
FROM table1
LEFT JOIN table2 ON columnA.id === table1.ex_id,
```

#### Right Outer Join
Any unmatched joins will be dropped, anything from `table2` will be joined.

```
SELECT column1, columnA
FROM table1
RIGHT JOIN table2 ON columnA.id === table1.ex_id,
```

#### Full Joins

Nothing will be throw away, all relevant columns will be set with a value of `null`

```
SELECT column1, columnA
FROM table1
FULL JOIN table2 ON columnA.id === table1.ex_id,
```

