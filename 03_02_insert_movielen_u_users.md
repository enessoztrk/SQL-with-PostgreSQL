
- Dataset: https://raw.githubusercontent.com/erkansirin78/datasets/master/ml-100k/u.user

- Download dataset
```
 curl -o u.user https://raw.githubusercontent.com/erkansirin78/datasets/master/ml-100k/u.user
```

- Explore first few lines
```
head u.user

1|24|M|technician|85711
2|53|F|other|94043
3|23|M|writer|32067
4|24|M|technician|43537
5|33|F|other|15213
6|42|M|executive|98101
7|57|M|administrator|91344
8|36|M|administrator|05201
9|29|M|student|01002
10|53|M|lawyer|90703

```

- Create a table

```
create table users
(user_id int primary key,
age smallint,
gender char(1),
occupation varchar,
zip_code char(5)
);
```

- Copy data into container
` docker cp u.user postgresql:/ ` 

- Insert data into table 
```
 docker exec -it postgresql \
 psql -d traindb -U train -c \
 "\copy public.users FROM '/u.user' DELIMITERS '|' CSV HEADER;"
 ```
 - Output ` COPY 942 ` 
 
 - Count query
 ```
 select count(distinct user_id) from users;
 ```
 
 - Output 
```
count|
-----+
  942|
```
 
 

 
 
 
 
 
 
 
```