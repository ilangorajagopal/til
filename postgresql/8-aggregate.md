# Grouping and Aggregate functions

While querying data in a table we can group records that have the same value.

For example, this is our table:

| create_date |             user_handle              | last_name | first_name |
| ----------- | ------------------------------------ | --------- | ---------- |
| 2021-08-27  | a61abfdc-434c-4865-8baa-367abe638432 | falconer  | quellcrist |
| 2021-08-27  | 8f5e5640-1074-4b5a-8f20-c3827609e8ab | kovacs    | takeshi    |
| 2021-08-27  | 9051a031-46cb-4d8a-8677-06ef58a2ca71 | bancroft  | laurens    |

To group records by date:

```shell
select count(*) from Users group by date;
```

This returns:

```shell
count
-------
     3
(1 row)
```

This is because all users were created on the same date. 

Postgres also has a few aggregate functions.

```shell
select min(date) from Users;
```

This returns the date with the lowest value. There are other aggregate functions like max, sum, and avg. 
