# SQL Notes

Notes / cheetsheet for remembering SQL commands.

Postgresql strings require single-quotes

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
JOIN table2 ON columnA.id = table1.ex_id,
```

#### Left Outer Join
Anything that does not match we will not drop it, anything from `table1` without a match will return a value of `null`

```
SELECT column1, columnA
FROM table1
LEFT JOIN table2 ON columnA.id = table1.ex_id,
```

#### Right Outer Join
Any unmatched joins will be dropped, anything from `table2` will be joined.

```
SELECT column1, columnA
FROM table1
RIGHT JOIN table2 ON columnA.id = table1.ex_id,
```

#### Full Joins

Nothing will be throw away, all relevant columns will be set with a value of `null`

```
SELECT column1, columnA
FROM table1
FULL JOIN table2 ON columnA.id = table1.ex_id,
```
#### Three Way Joins

`columnAlpha` is from a third table, 

```
SELECT column1, columnA, columnAlpha
FROM table1
JOIN table2 ON columnA.id = table1.ex_id,
JOIN table3 ON table3.ex_id = table2.user_id AND table3.id = columnA.ex_id
```

## Grouping and Aggregates

### Grouping
Reduces many rows down to a few rows, done by using the `GROUP BY` keyword. 

Example Table:
```
    +-------------+--------------+-------+------------+
    | name        | manufacturer | price | units_sold |
    +-------------+--------------+-------+------------+
    | N1280       | Nokia        | 199   | 1925       |
    +-------------+--------------+-------+------------+
    | Iphone 4    | Apple        | 399   | 9436       |
    +-------------+--------------+-------+------------+
    | Galaxy S    | Samsung      | 299   | 2359       |
    +-------------+--------------+-------+------------+
```

```
  SELECT manufacturer
  FROM phones
  GROUP BY manufacturer;
```


### Aggregates
Reduces many values down to one, done by using `aggregate` functions

- `COUNT(num)` -> Returns the number of values in a group
- `SUM(num)` -> Finds the sum of a group of numbers
- `AVG(num)` -> Finds the average of a group of numbers
- `MIN(num)` -> Finds the minimum value of a group of numbers
- `MAX(num)` -> Finds the maximum value of a group of numbers