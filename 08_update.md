
## DANGER
If you omit the WHERE clause, ALL records will be updated!

## 1. UPDATE a record
### Increase Santé Gourmet's income to 54000

- Select and see where to update
```
select * from customers where customer_name = 'Santé Gourmet';
```

- Output
```
customer_id|customer_name|contact_name    |address               |city   |postalcode|country|income |
-----------+-------------+----------------+----------------------+-------+----------+-------+-------+
         70|Santé Gourmet|Jonas Bergulfsen|Erling Skakkes gate 78|Stavern|4110      |Norway |19350.0|
```

- Now update
```
update customers set income = 54000 where customer_id = 70;
```

- See result
```
select * from customers where customer_name = 'Santé Gourmet';


customer_id|customer_name|contact_name    |address               |city   |postalcode|country|income |
-----------+-------------+----------------+----------------------+-------+----------+-------+-------+
         70|Santé Gourmet|Jonas Bergulfsen|Erling Skakkes gate 78|Stavern|4110      |Norway |54000.0|
``` 


## 2. UPDATE multiple rows
### Increase income 5000 in country Italy

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

- Update now
```
update customers set income = income + 5000 where country = 'Italy';
```

- See result
```
select * from customers where country = 'Italy';


customer_id|customer_name               |contact_name    |address                |city         |postalcode|country|income |
-----------+----------------------------+----------------+-----------------------+-------------+----------+-------+-------+
         27|Franchi S.p.A.              |Paolo Accorti   |Via Monte Bianco 34    |Torino       |10100     |Italy  |36320.0|
         49|Magazzini Alimentari Riuniti|Giovanni Rovelli|Via Ludovico il Moro 22|Bergamo      |24100     |Italy  |22500.0|
         66|Reggiani Caseifici          |Maurizio Moroni |Strada Provinciale 124 |Reggio Emilia|42100     |Italy  |23980.0|
``` 
