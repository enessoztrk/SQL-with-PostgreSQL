- Download data 
``` 
curl -o name.basics.tsv.gz  https://datasets.imdbws.com/name.basics.tsv.gz 

gunzip name.basics.tsv.gz
``` 

- Explore first few lines
```
 head name.basics.tsv
nconst  primaryName     birthYear       deathYear       primaryProfession       knownForTitles
nm0000001       Fred Astaire    1899    1987    soundtrack,actor,miscellaneous  tt0072308,tt0050419,tt0053137,tt0031983
nm0000002       Lauren Bacall   1924    2014    actress,soundtrack      tt0071877,tt0038355,tt0117057,tt0037382
nm0000003       Brigitte Bardot 1934    \N      actress,soundtrack,music_department     tt0049189,tt0054452,tt0057345,tt0056404
nm0000004       John Belushi    1949    1982    actor,soundtrack,writer tt0077975,tt0080455,tt0072562,tt0078723
nm0000005       Ingmar Bergman  1918    2007    writer,director,actor   tt0069467,tt0083922,tt0060827,tt0050986
nm0000006       Ingrid Bergman  1915    1982    actress,soundtrack,producer     tt0034583,tt0077711,tt0038109,tt0036855
nm0000007       Humphrey Bogart 1899    1957    actor,soundtrack,producer       tt0034583,tt0043265,tt0037382,tt0033870
nm0000008       Marlon Brando   1924    2004    actor,soundtrack,director       tt0078788,tt0070849,tt0068646,tt0047296
nm0000009       Richard Burton  1925    1984    actor,soundtrack,producer       tt0057877,tt0059749,tt0061184,tt0087803
```

- Create a table

```
create table public.name_basics(
nconst  varchar primary key,
primary_name varchar,       
birth_year varchar,
death_year varchar,
primary_profession varchar,
known_for_titles varchar
);
```

- Why this schema?
	- years are expected to be integer but they contain character
	- After cleaning types can be casted.

- Copy data into container
` docker cp name.basics.tsv postgresql:/ ` 

- Insert data into table 
```
 docker exec -it postgresql \
 psql -d traindb -U train -c \
 "\copy public.name_basics FROM '/name.basics.tsv' DELIMITERS E'\t' CSV HEADER;"
 ```
 - Output ` COPY 11410275 ` 
 
 - Count query
 ```
 select count(1) from public.name_basics; 
 ```
 
 - Output 
```
count   |
--------+
11410275|
```
 