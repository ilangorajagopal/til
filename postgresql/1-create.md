# create

Creates a table in the database

```shell
create table Users ( create_date date, userid uuid, last_name text, first_name text );
```

We can enter the columns on different lines using `Shift + Enter`. When we do this postgres will wait for the semicolon to run the command.

The above command creates a new table called `Users`. The table will have the following columns: `create_date`, `userid`, `last_name` and `first_name`.

The column names are followed by the data types. There are many more data types supported by postgres which I will cover in a future entry.