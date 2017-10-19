---
title: TEXT Type
summary: String of Unicode characters.
toc: false
---

## Synopsis
`TEXT` datatype is used to specify data of a string of unicode characters.

## Syntax
```
type_specification ::= TEXT | VARCHAR

text_literal ::= "'" [ letter ...] "'"
```

Where 

- `TEXT` and `VARCHAR` are aliases.
- `letter` is any character except for single quote (`[^']`)

## Semantics

- Columns of type `TEXT` or `VARCHAR` can be part of the `PRIMARY KEY`.
- Implicitly, value of type `TEXT` datatype are neither convertible nor comparable to non-text datatypes.
- The length of `TEXT` string is virtually unlimited.

## Examples

``` sql
cqlsh:example> CREATE TABLE users(user_name TEXT PRIMARY KEY, full_name VARCHAR);
cqlsh:example> INSERT INTO users(user_name, full_name) VALUES ('jane', 'Jane Doe');
cqlsh:example> INSERT INTO users(user_name, full_name) VALUES ('john', 'John Doe');
cqlsh:example> UPDATE users set full_name = 'Jane Poe' WHERE user_name = 'jane';
cqlsh:example> SELECT * FROM users;

 user_name | full_name
-----------+-----------
      jane |  Jane Poe
      john |  John Doe
```

## See Also

[Data Types](..#datatypes)