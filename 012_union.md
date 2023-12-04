The UNION operator is used to combine the result-set of two or more SELECT statements.

Every SELECT statement within UNION must have the same number of columns
The columns must also have similar data types
The columns in every SELECT statement must also be in the same order


## 1.UNION
```
select * from orders 
union
select * from orders;
```

- Output
```
order_id|customer_id|employee_id|order_date|shipper_id|
--------+-----------+-----------+----------+----------+
   10308|          2|          7|1996-09-18|         3|
   10309|         37|          3|1996-09-19|         1|
   10310|         77|          8|1996-09-20|         2|
```


## 2.UNION ALL
```
select * from orders 
union all
select * from orders;
```

- Output
```
order_id|customer_id|employee_id|order_date|shipper_id|
--------+-----------+-----------+----------+----------+
   10308|          2|          7|1996-09-18|         3|
   10309|         37|          3|1996-09-19|         1|
   10310|         77|          8|1996-09-20|         2|
   10308|          2|          7|1996-09-18|         3|
   10309|         37|          3|1996-09-19|         1|
   10310|         77|          8|1996-09-20|         2|
```