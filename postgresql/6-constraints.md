# constraints

When creating tables, it's important to set constraints to our data. There are multiple constraints that we can set to columns.

```shell
create table Users ( date date not null, userid uuid primary key, email not null unique, last_name text, first_name text not null );
```

There are many things happening here. In the `Users` table, we're setting `not null` to columns.
If any of those columns are null for a record, Postgres will throw an error.

We're setting the `primary key` constraint for `userid` column which means that each record will have unique `userid` values and it cannot be null.
It will also be the way we retrieve, update or delete that record.

For `email` we're setting a `unique` constraint which means each record will have a unique value.