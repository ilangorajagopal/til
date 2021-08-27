# Indexes

Index improves performance of a database. Indexes allows our database to find and retrieve specific rows much faster than it could do without an index.

```shell
create index test1_userid on Users (userid);
```

We have to pick and choose when to use index. Indexes should be avoided when the table is small, there are large batch of insert operations, and where columns are frequently manipulated.
Indexing in these cases causes overhead and actually degrades performance.