

## 1.SHOW tables
```
select table_catalog, table_schema, table_name   
from INFORMATION_SCHEMA.tables
where table_catalog = 'traindb' and table_schema = 'public';
```

- Output
```
table_catalog|table_schema|table_name      |
-------------+------------+----------------+
traindb      |public      |student         |
traindb      |public      |movies          |
traindb      |public      |users           |
traindb      |public      |ratings         |
traindb      |public      |customers_gt_50k|
traindb      |public      |name_basics     |
traindb      |public      |orders          |
traindb      |public      |customers       |
```

## 2. backup movielens tables
```
select * into ratings_bckp
from ratings;

select * into users_bckp
from users;

select * into movies_bckp
from movies;
```

## 3. Foreign key constraint
A foreign key is a column or a group of columns in a table that reference the primary key of another table.
The table that contains the foreign key is called the referencing table or child table (ratings). 
And the table referenced by the foreign key is called the referenced table or parent table (movies, users).

### 3.1. For users
```
ALTER TABLE ratings 
ADD CONSTRAINT fk_user_id 
FOREIGN KEY (user_id) 
REFERENCES users (user_id)
on delete cascade;
```

### 3.2. For movies
```
ALTER TABLE ratings 
ADD CONSTRAINT fk_item_id 
FOREIGN KEY (item_id) 
REFERENCES movies (movieid)
on delete cascade;
```

## 4. See rating for movieid 1000
``` 
select * from ratings r where item_id = 1000;
```

- Output
```
user_id|item_id|rating|rating_time|
-------+-------+------+-----------+
     87|   1000|     3|  879877173|
    279|   1000|     4|  875314313|
    125|   1000|     3|  892838977|
    417|   1000|     4|  879648403|
    393|   1000|     3|  889731139|
    497|   1000|     2|  878759777|
     22|   1000|     3|  878886333|
    276|   1000|     2|  877935262|
    642|   1000|     3|  885602340|
    880|   1000|     3|  880175128|
```

## 5. See movie 1000 from movies
```
select movieid, movietitle 
from movies m where movieid = 1000;

movieid|movietitle         |
-------+-------------------+
   1000|LightningJack(1994)|
```

## 6. Delete movieid 1000 from movies
```
delete from movies where movieid = 1000;

user_id|item_id|rating|rating_time|
-------+-------+------+-----------+
```