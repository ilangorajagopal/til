# where

Using the where clause we can filter data based on certain conditions

```shell
select * from Users where last_name = 'kovacs';
```

We can also combine multiple filters using the `and` and `or` operators.

We can also use comparison operators like <, >, <=, >=, and <> (not equal).

When checking for empty values, we have to use the `is` operator.

```shell
select * from Users where first_name is null;
```

Another filter is the `between` operator that lets us check if a value falls within a range of values.

There's also the `in` operator which checks if a column has one of the value from a specified list:

```shell
select * from Users where last_name in ('falconer', 'kovacs');
```