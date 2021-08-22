# select

Select will list the rows from a table that matches the given filter.

```shell
select * from Users;
```

This will list all the rows from the `Users` table.

We can also choose which columns are returned.

```shell
select first_name, last_name from Users;
```

If we specify a column that does not exist in our table, postgres will throw an error.

Postgres comes with a few built-in functions that can be used with the `select` command.

Display the number of rows in the table:

```shell
select count(*) from Users;
```

Display the rows that have a distinct value for a columns

```shell
select distinct(first_name) from Users;
```

We can also combine multiple functions to display rows in unique ways

```shell
select count(distinct(last_name)) from Users;
```

The above command will return the number of rows that have a distinct last name values. In other words, it removes duplicates from the count.
