## Prepare the data 
```
delete from customers where customer_id = 77;
```

## Inner join 
```
select o.customer_id, o.order_date, c.customer_id,  c.customer_name
from public.orders o
join public.customers c 
on o.customer_id = c.customer_id;
```

- Output:
```
customer_id|order_date|customer_id|customer_name                     |
-----------+----------+-----------+----------------------------------+
          2|1996-09-18|          2|Ana Trujillo Emparedados y helados|
         37|1996-09-19|         37|Hungry Owl All-Night Grocers      |
```


## Left join 
```
select o.customer_id, o.order_date, c.customer_id,  c.customer_name
from public.orders o
left join public.customers c 
on o.customer_id = c.customer_id;
```

- Output
```
customer_id|order_date|customer_id|customer_name                     |
-----------+----------+-----------+----------------------------------+
          2|1996-09-18|          2|Ana Trujillo Emparedados y helados|
         37|1996-09-19|         37|Hungry Owl All-Night Grocers      |
         77|1996-09-20|           |                                  |
```


## Right join 
```
select o.customer_id, o.order_date, c.customer_id,  c.customer_name
from public.orders o
right join public.customers c 
on o.customer_id = c.customer_id
limit 5;
```

- Output
``` 
customer_id|order_date|customer_id|customer_name                     |
-----------+----------+-----------+----------------------------------+
          2|1996-09-18|          2|Ana Trujillo Emparedados y helados|
         37|1996-09-19|         37|Hungry Owl All-Night Grocers      |
           |          |         20|Ernst Handel                      |
           |          |         82|Trail's Head Gourmet Provisioners |
           |          |         25|Frankenversand                    |
```

## Full join (full outer join)
```
select o.customer_id, o.order_date, c.customer_id,  c.customer_name
from public.orders o
full join public.customers c 
on o.customer_id = c.customer_id
limit 5;
```

- Output
```
customer_id|order_date|customer_id|customer_name                     |
-----------+----------+-----------+----------------------------------+
          2|1996-09-18|          2|Ana Trujillo Emparedados y helados|
         37|1996-09-19|         37|Hungry Owl All-Night Grocers      |
         77|1996-09-20|           |                                  |
           |          |         20|Ernst Handel                      |
           |          |         82|Trail's Head Gourmet Provisioners |
```
































