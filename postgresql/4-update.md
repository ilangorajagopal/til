# update

Our `Users` table has only one row. Let's add one more:

```shell
insert into Users values (now(), 'cc4ac548-f285-4f02-93e2-7a53664d20ee', 'kovacs', 'takeshi');
```

The `userid` value is the same as the previous record.

| create_date |             user_handle              | last_name | first_name |
| ----------- | ------------------------------------ | --------- | ---------- |
| 2021-08-22  | cc4ac548-f285-4f02-93e2-7a53664d20ee | falconer  | quellcrist |
| 2021-08-22  | cc4ac548-f285-4f02-93e2-7a53664d20ee | kovacs    | takeshi    |

Postgres doesn't have a built-in way to generate uuid but there is an extension that we can use called `uuid-ossp`.

To add the extension:

```shell
create extension "uuid-ossp";
```

Now we can use `uuid_generate_v4()` to automatically generate a unique uuid for our records.

To update the existing ones with unique uuids, we can run this:

```shell
update Users set userid = uuid_generate_v4();
```

This will update all our records with a unique uuid. 

We can choose which records to update using the `where` keyword:

```shell
update Users set userid = uuid_generate_v4() where last_name = 'kovacs';
```

We can also update multiple columns at a time:

```shell
update Users set userid = uuid_generate_v4(), first_name = 'takeshi' where last_name = 'kovacs';
```