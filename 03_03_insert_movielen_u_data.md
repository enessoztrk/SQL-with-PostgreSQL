
- Dataset: https://raw.githubusercontent.com/erkansirin78/datasets/master/ml-100k/u.data

- Download dataset
```
curl -o u.data https://raw.githubusercontent.com/erkansirin78/datasets/master/ml-100k/u.data
```

- Explore first few lines
```
head u.data

user_id item_id rating  timestamp
196     242 3   881250949
186     302 3   891717742
22      377 1   878887116
244     51  2   880606923
166     346 1   886397596
298     474 4   884182806
115     265 2   881171488
253     465 5   891628467
305     451 3   886324817
```

- Create a table

```
create table public.ratings(
user_id int,
item_id int, 
rating smallint,
rating_time bigint,
primary key(user_id, item_id)
);
```

- Copy data into container
` docker cp u.data postgresql:/ ` 

- Insert data into table 
```
 docker exec -it postgresql \
 psql -d traindb -U train -c \
 "\copy public.ratings FROM '/u.data' DELIMITERS E'\t' CSV HEADER;"
 ```
 - Output ` COPY 100000 ` 
 
 - Count query
 ```
 select count(distinct(user_id, item_id)) from ratings; 
 ```
 
 - Output 
```
count |
------+
100000|
```
 
 

 
 
 
 
 
 
 
```