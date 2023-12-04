## 1. Query without index
- Find Cüneyt Arkin
```
select *
from public.name_basics 
where primaryname = 'Cüneyt Arkin';
```

- Response Time: 5.92 secs


## 2. Create an index 
```
CREATE INDEX idx_primary_name 
ON public.name_basics using hash(primary_name);
```

## 3. Query after index
- Now try again
```
select *
from public.name_basics 
where primaryname = 'Cüneyt Arkin';
```
- Response Time: 5 ms

- Turkan Soray
```
select *
from public.name_basics 
where primaryname = 'Türkan Soray';
```
- Response Time: 2 ms

## 4. primary keys have natural index 
- Get Clint Eastwood with primary key 
```
select *
from public.name_basics 
where nconst = 'nm0000142';
```

- Response Time: 5 ms