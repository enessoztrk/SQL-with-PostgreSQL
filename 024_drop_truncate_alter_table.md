

## 1. DROP
```
drop table if exists test ;
create table if not exists 
test(id int, name varchar, age varchar);

insert into test values(1, 'Tüzün', '23'), (2, 'Muhsin', '33');
drop table test;
```

## 2. TRUNCATE
```
create table test(id int, name varchar, age varchar);

insert into test values(1, 'Tüzün', '23'), (2, 'Muhsin', '33');

select * from test;

truncate table test;

select * from test;
```

## 3. ALTER
` insert into test values(1, 'Tüzün', '23'), (2, 'Muhsin', '33'); ` 

### 3.1. ADD Column
```
alter table test add column surname varchar;

select * from test;

update test set surname = 'Berrak' where name ='Tüzün';

select * from test;

update test set surname = 'Kutlu' where name ='Muhsin';

select * from test;
```

### 3.2. ALTER/MODIFY COLUMN
```
alter table test 
ALTER COLUMN age TYPE int
using age::int;

select * from test;

select column_name, data_type
from INFORMATION_SCHEMA.COLUMNS 
where table_name = 'test';
```

### 3.3. DROP COLUMN
```
alter table test drop column surname;

select * from test;
```