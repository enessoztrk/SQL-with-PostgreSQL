creates and inserts records into new table from result of select query.
It doesn't work if there is already a table. If there is a table use INSERT INTO SELECT.

-Row count of customers table
```
select count(1) from customers ;
```

- Output
```
count|
-----+
   88|
```


## 1. SELECT INTO  (CREATE + INSERT)
- Create another table income gt 50000.
```
SELECT * INTO customers_gt_50k
FROM customers
WHERE income > 50000;
```

- Check new table
```
select customer_name, income from customers_gt_50k limit 10;
```

- Output
```
customer_name                     |income |
----------------------------------+-------+
Alfreds Futterkiste               |67470.0|
Ana Trujillo Emparedados y helados|79210.0|
Around the Horn                   |64720.0|
Bon app'                          |59430.0|
Bottom-Dollar Marketse            |67550.0|
Cactus Comidas para llevar        |56070.0|
Centro comercial Moctezuma        |90880.0|
Chop-suey Chinese                 |64840.0|
Comércio Mineiro                  |85250.0|
Drachenblut Delikatessend         |70310.0|
```

- Check count of new table
```
select count(1) from customers_gt_50k; 

count|
-----+
   47|
```

## 2. INSERT INTO SELECT (INSERT INTO EXISTING TABLE)
- Insert income between 40000 and 50000
```
INSERT INTO customers_gt_50k
SELECT * FROM customers
WHERE income between 40000 and 50000;
```
- Check row count
``` 
select count(1) from customers_gt_50k; 
```

- Output
```
count|
-----+
   55|
```
- 8 more rpws added. Nothing happeed existing rows.