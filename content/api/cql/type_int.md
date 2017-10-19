---
title: Integer Types
summary: Signed integers of different ranges
---

## Synopsis
There are several different datatypes for integers of different value ranges. Integers can be set, inserted, incremented, and decremented while `COUNTER` can only be incremented or decremented. We've extend Apache Cassandra to support increment and decrement operator for integer datatypes.

DataType | Min | Max |
---------|-----|-----|
`TINYINT` | -128 | 127 |
`SMALLINT` | -2,147,483,648 | 2,147,483,647 |
`INT` or `INTEGER` | -32,768 | 32,767 |
`BIGINT` | -2,147,483,648 | 2,147,483,647 |
`COUNTER` | -2,147,483,648 | 2,147,483,647 |

## Syntax
The following keywords are used to specify a column of type integer for different constraints including its value ranges.

```
type_specification ::= TINYINT | SMALLINT | INT | INTEGER | BIGINT | COUNTER

integer_literal ::= [ + | - ] digit [ { digit | , } ... ]
```

## Semantics

- Columns of type `TINYINT`, `SMALLINT`, `INT`, `INTEGER`, or `BIGINT` can be part of the `PRIMARY KEY`.
- Values of different integer datatypes are comparable and convertible to one another.
- Values of integer datatypes are convertible but not comparable to floating point number.
- Values of floating point datatypes are not convertible to integers.

### Counter DataType
`COUNTER` is an alias of `BIGINT` but has additional constraints.

- Columns of type `COUNTER` cannot be part of the`PRIMARY KEY`.
- If a column is of type `COUNTER`, all non-primary-key columns must also be of type `COUNTER`.
- Column of type `COUNTER` cannot be set or inserted. They must be incremented or decremented.
- If a column of type `COUNTER` is NULL, its value is replaced with zero when incrementing or decrementing.

## Examples

### Using integer datatypes

``` sql
cqlsh:example> CREATE TABLE items(id INT PRIMARY KEY, item_count BIGINT);
cqlsh:example> INSERT INTO items(id, item_count) VALUES(1, 1);
cqlsh:example> INSERT INTO items(id, item_count) VALUES(2, 2);
cqlsh:example> UPDATE items SET item_count = 5 WHERE id = 1;
cqlsh:example> UPDATE items SET item_count = item_count + 1 WHERE id = 2;
cqlsh:example> SELECT * FROM items;

 id | item_count
----+------------
  2 |          3
  1 |          5
```

### Using `COUNTER` datatype

``` sql
cqlsh:example> CREATE TABLE item_counters(id INT PRIMARY KEY, item_counter COUNTER);
cqlsh:example> -- For counter type, null values are treated as 0.
cqlsh:example> UPDATE item_counters SET item_counter = item_counter + 1 WHERE id = 1;
cqlsh:example> SELECT * FROM item_counters;

 id | item_counter
----+--------------
  1 |            1
```

## See Also

[Data Types](..#datatypes)