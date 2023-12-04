## 1. INSERT INTO all columns
```
INSERT INTO customers (customer_name, contact_name, address, city, postalcode, country, income)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway', 38500);
```
## 2. INSERT INTO some columns

```
INSERT INTO customers (customer_name, city, country)
VALUES ('Cardinal', 'Stavanger', 'Norway');
```

## 3. See results
```
select * from customers where country = 'Norway';
```

- Output
```
customer_id|customer_name|contact_name    |address               |city     |postalcode|country|income |
-----------+-------------+----------------+----------------------+---------+----------+-------+-------+
         70|Santé Gourmet|Jonas Bergulfsen|Erling Skakkes gate 78|Stavern  |4110      |Norway |19350.0|
         92|Cardinal     |Tom B. Erichsen |Skagen 21             |Stavanger|4006      |Norway |38500.0|
         93|Cardinal     |                |                      |Stavanger|          |Norway |       |
```
- When inserting only some columns, remaining columns inserted with default values.
- Since customer_id auto increment (serial) no need any explicit insert.


## 4. NULL
```
select * from customers where country = 'Norway' and income is NULL;
```

- Output
```
customer_id|customer_name|contact_name|address|city     |postalcode|country|income|
-----------+-------------+------------+-------+---------+----------+-------+------+
         93|Cardinal     |            |       |Stavanger|          |Norway |      |
```

## 5. NOT NULL
```
select * from customers where country = 'Norway' and income is NOT NULL;
```

- Output
```
customer_id|customer_name|contact_name    |address               |city     |postalcode|country|income |
-----------+-------------+----------------+----------------------+---------+----------+-------+-------+
         70|Santé Gourmet|Jonas Bergulfsen|Erling Skakkes gate 78|Stavern  |4110      |Norway |19350.0|
         92|Cardinal     |Tom B. Erichsen |Skagen 21             |Stavanger|4006      |Norway |38500.0|
```







