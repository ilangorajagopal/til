# join

We can't fit all of our data in one table so we split up data into multiple tables but in our applications we might need data from multiple data combined.

To do this we can use `join`.

Here's our Users table:

    date    |                userid                | last_name | first_name 
------------+--------------------------------------+-----------+------------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist

and our Purchases table:

    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1


If we wanted to query the purchases made by users, we could query each table separately but that is inefficient. We could use `join` to combine the data in two tables based on certain conditions.

For example, this query joins the user and purchases table data:

```shell
select * from Users u left outer join Purchases p on u.userid = p.userid;
```

    date    |                userid                | last_name | first_name |    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+-----------+------------+------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1


Our query starts off with the Users table data and joins it with the purchases table on the condition that the `userid` column values are equal. If we add a new user and do the join query again:


    date    |                userid                | last_name | first_name |    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+-----------+------------+------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1
2021-08-31 | fe66dc9d-15f5-44de-88b2-59c35cf56a67 | elliot    | vernon     |            |                                      |                                      |         

The newly added user doesn't have any purchases so the columns from the purchases table for that user are null. This is because, we used a `left outer join`. It takes the first table and tries to match to columns to the second table. If there are no matching records, it returns null.

Alternatively if we use a `right outer join`, we won't see the newly added user because the query starts with the second table and tries to map it to the first. Since there are no purchase record for the new user, they don't show up.

```shell
select * from Users u right outer join Purchases p on u.userid = p.userid;
```


    date    |                userid                | last_name | first_name |    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+-----------+------------+------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1

If we want to return everything from both tables, we can use a `full outer join`:

```shell
select * from Users u full outer join Purchases p on u.userid = p.userid;
```

    date    |                userid                | last_name | first_name |    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+-----------+------------+------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1
2021-08-31 | fe66dc9d-15f5-44de-88b2-59c35cf56a67 | elliot    | vernon     |            |                                      |                                      |         


Then there's a cross join, which joins both ways:


```shell
select * from Users u cross join Purchases p;
```

    date    |                userid                | last_name | first_name |    date    |                userid                |                 sku                  | quantity 
------------+--------------------------------------+-----------+------------+------------+--------------------------------------+--------------------------------------+----------
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | fe66dc9d-15f5-44de-88b2-59c35cf56a67 | elliot    | vernon     | 2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | d1ea9810-b2c7-4b32-986b-e20f35d2c760 |        2
2021-08-31 | 4f64c0d1-fd9e-4240-a1ab-f27f01fa6c00 | kovacs    | takeshi    | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1
2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | falconer  | quellcrist | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1
2021-08-31 | fe66dc9d-15f5-44de-88b2-59c35cf56a67 | elliot    | vernon     | 2021-08-31 | 94e5b8d9-c63b-4aff-b0e5-46b9cfa1f900 | 1081d9dd-eec9-44ad-9699-53ff37d08241 |        1

