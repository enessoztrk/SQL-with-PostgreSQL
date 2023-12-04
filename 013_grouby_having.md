The GROUP BY statement groups rows that have the same values into summary rows, like "find the number of customers in each country".

The GROUP BY statement is often used with aggregate functions (COUNT(), MAX(), MIN(), SUM(), AVG()) to group the result-set by one or more columns.

## 1. GROUP BY and COUNT
- How many customers each country has?
```
select country, count(customer_id)
from customers 
group by country
order by count desc;
```

- Output
```
country    |count|
-----------+-----+
USA        |   12|
Germany    |   11|
France     |   11|
Brazil     |    9|
UK         |    7|
Mexico     |    5|
Spain      |    5|
Venezuela  |    4|
Argentina  |    3|
Canada     |    3|
Sweden     |    2|
Austria    |    2|
Finland    |    2|
Norway     |    2|
Belgium    |    2|
Switzerland|    2|
Denmark    |    2|
Portugal   |    2|
Poland     |    1|
Ireland    |    1|
```


## 2. GROUP BY AVG
- Average income by country.
```
select country, avg(income)
from customers 
group by country
order by avg desc;
```

- Output
```
country    |avg               |
-----------+------------------+
Brazil     | 81086.66666666667|
Mexico     |           78248.0|
Venezuela  |           77632.5|
Ireland    |           75500.0|
Canada     |           75130.0|
Portugal   |           65255.0|
Argentina  |57393.333333333336|
Switzerland|           54680.0|
USA        |50509.166666666664|
Belgium    |           49865.0|
UK         | 49398.57142857143|
Denmark    |           49080.0|
Germany    | 48856.36363636364|
Spain      |           47098.0|
France     |41398.181818181816|
Norway     |           38500.0|
Poland     |           31670.0|
Austria    |           27880.0|
Finland    |           24080.0|
Sweden     |           20800.0|
```

## 3. GROUP BY COUNT and AVG
- Average income by country.
```
select country, avg(income), count(customer_id)
from customers 
group by country
order by avg desc;
```

- Output
```
country    |avg               |count|
-----------+------------------+-----+
Brazil     | 81086.66666666667|    9|
Mexico     |           78248.0|    5|
Venezuela  |           77632.5|    4|
Ireland    |           75500.0|    1|
Canada     |           75130.0|    3|
Portugal   |           65255.0|    2|
Argentina  |57393.333333333336|    3|
Switzerland|           54680.0|    2|
USA        |50509.166666666664|   12|
Belgium    |           49865.0|    2|
UK         | 49398.57142857143|    7|
Denmark    |           49080.0|    2|
Germany    | 48856.36363636364|   11|
Spain      |           47098.0|    5|
France     |41398.181818181816|   11|
Norway     |           38500.0|    2|
Poland     |           31670.0|    1|
Austria    |           27880.0|    2|
Finland    |           24080.0|    2|
Sweden     |           20800.0|    2|
```

## 4. HAVING
The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions.

- Try to use where for filter
```
select country, avg(income), count(customer_id)
from customers 
group by country
where country in ('USA', 'Sweden', 'Brazil')
order by avg desc;
```
- Output
```
SQL Error [42601]: ERROR: syntax error at or near "where"
  Position: 104
```

- Use having
```
select country, avg(income), count(customer_id)
from customers 
group by country
having country in ('USA', 'Sweden', 'Brazil')
order by avg desc;
```

- Output
```
country|avg               |count|
-------+------------------+-----+
Brazil | 81086.66666666667|    9|
USA    |50509.166666666664|   12|
Sweden |           20800.0|    2|
```