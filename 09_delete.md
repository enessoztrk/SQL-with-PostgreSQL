
## DANGER
If you omit the WHERE clause, ALL records will be deleted!

## 1.DELETE a record
### Increase Santé Gourmet's

- Select and find the id
```
select * from customers where customer_name = 'Santé Gourmet';
```

- Output
```
customer_id|customer_name|contact_name    |address               |city   |postalcode|country|income |
-----------+-------------+----------------+----------------------+-------+----------+-------+-------+
         70|Santé Gourmet|Jonas Bergulfsen|Erling Skakkes gate 78|Stavern|4110      |Norway |19350.0|
```

- Now delete
```
delete from customers where customer_id = 70;
```

- See result
```
select * from customers where customer_name = 'Santé Gourmet';


customer_id|customer_name|contact_name|address|city|postalcode|country|income|
-----------+-------------+------------+-------+----+----------+-------+------+
``` 


## 2. DELETE multiple rows
### Delete country Italy

- See which rows will be affected
```
select * from customers where country = 'Italy';
```

- Output
```
customer_id|customer_name               |contact_name    |address                |city         |postalcode|country|income |
-----------+----------------------------+----------------+-----------------------+-------------+----------+-------+-------+
         27|Franchi S.p.A.              |Paolo Accorti   |Via Monte Bianco 34    |Torino       |10100     |Italy  |31320.0|
         49|Magazzini Alimentari Riuniti|Giovanni Rovelli|Via Ludovico il Moro 22|Bergamo      |24100     |Italy  |17500.0|
         66|Reggiani Caseifici          |Maurizio Moroni |Strada Provinciale 124 |Reggio Emilia|42100     |Italy  |18980.0|
```

- Delete now
```
delete from customers where country = 'Italy';
```

- See result
```
select * from customers where country = 'Italy';


customer_id|customer_name|contact_name|address|city|postalcode|country|income|
-----------+-------------+------------+-------+----+----------+-------+------+
``` 
