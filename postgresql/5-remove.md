# remove

I've added another record to our `Users` table. Here's the table:

| create_date |             user_handle              | last_name | first_name |
| ----------- | ------------------------------------ | --------- | ---------- |
| 2021-08-22  | 48ef3b9f-616f-4086-be9f-cd81ceab481c | falconer  | quellcrist |
| 2021-08-22  | c665a06c-69d8-43bb-bc84-3f9ce54b77e7 | kovacs    | takeshi    |
| 2021-08-22  | 2ffc5d8a-2a4f-418b-9ae8-b4e2bd3dd584 | ortega    | kristin    |

Let's remove the last row:

```shell
delete from Users where last_name = 'ortega';
```

This deletes the matching records from the table.

The `delete` command loops over the records so if we don't specify a `where` clause, it will delete all the rows.

We can specify multiple filters for `where` using `and` or `or`.

We can also remove all the records from our table using the `truncate` command:

```shell
truncate Users;
```

To delete the entire table:

```shell
drop table Users;
```