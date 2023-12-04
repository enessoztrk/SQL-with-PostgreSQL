## 1. CASE
```
SELECT customer_name, income,
CASE
    WHEN income < 30000 THEN 'Low income'
    WHEN income between 30000 and 60000 THEN 'Middle income'
    ELSE 'High income'
END AS income_class
FROM customers
limit 10;
```

- Output
```
customer_name                     |income |income_class |
----------------------------------+-------+-------------+
Alfreds Futterkiste               |67470.0|High income  |
Ana Trujillo Emparedados y helados|79210.0|High income  |
Antonio Moreno Taquería           |45090.0|Middle income|
Around the Horn                   |64720.0|High income  |
Berglunds snabbköp                |30150.0|Middle income|
Blauer See Delikatessen           |16860.0|Low income   |
Blondel père et fils              |12090.0|Low income   |
Bólido Comidas preparadas         |32150.0|Middle income|
Bon app'                          |59430.0|Middle income|
Bottom-Dollar Marketse            |67550.0|High income  |
```