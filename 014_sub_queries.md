## 1. 
- Select customer with max income in USA.
```
select customer_name, income, city, country from customers 
where income = 
(select max(income) from customers where country = 'USA');
```

- Output
```
customer_name             |income |city       |country|
--------------------------+-------+-----------+-------+
Rattlesnake Canyon Grocery|93560.0|Albuquerque|USA    |
```