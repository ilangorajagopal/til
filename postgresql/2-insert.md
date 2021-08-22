# insert

Inserts a "record" into a table.

```shell
insert into Users (create_date, userid, last_name, first_name) values ('2021-08-22', 'cc4ac548-f285-4f02-93e2-7a53664d20ee', 'falconer', 'quellcrist');
```

This will create a record or row in the table with the given values. If we specify the columns, we have to define the values in that order.
It's considered best practice to do this. We can also skip the columns. If we skip the columns, we have to define the values in the order that we created the columns in the `create` command.

```shell
insert into Users values ('2021-08-22', 'cc4ac548-f285-4f02-93e2-7a53664d20ee', 'falconer', 'quellcrist');
```

If the column data types and values don't match, postgres will throw an error.

Postgres also comes with functions that can do some actions, like creating timestamps.

```shell
insert into Users values (now(), 'cc4ac548-f285-4f02-93e2-7a53664d20ee', 'falconer', 'quellcrist');
```

Doing any of the above results in a new row added to the `Users` table.

| create_date |             user_handle              | last_name | first_name |
| ----------- | ------------------------------------ | --------- | ---------- |
| 2021-08-22  | cc4ac548-f285-4f02-93e2-7a53664d20ee | falconer  | quellcrist |

