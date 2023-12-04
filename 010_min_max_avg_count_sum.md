
## 1. MIN and MAX
- Select MIN and MAX income
```
select min(income) as min_income, max(income) as max_income 
from customers ;
```

- Output
```
min_income|max_income|
----------+----------+
   10690.0|   98690.0|
```


## 2. COUNT, AVG, SUM
```
select count(customer_id) as row_count, avg(income) as mean_income, sum(income) as sum_income
from customers ;
```

- Output
```
row_count|mean_income      |sum_income|
---------+-----------------+----------+
       89|54092.84090909091| 4760170.0|
```