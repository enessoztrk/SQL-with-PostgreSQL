


## Primary key, foreign key 

## ratings and movies relation 

## Inner join of two table
```
select * from 
ratings r 
join movies m on r.item_id = m.movieid
limit 10;
```

- Output
```
user_id|item_id|rating|rating_time|movieid|movietitle                                                    |releasedate|videoreleasedate|imdburl                                                                                                                               |unknown|action|adventure|animation|childrens|comedy|crime|documentary|drama|fantasy|filmnoir|horror|musical|mystery|romance|scifi|thriller|war|western|
-------+-------+------+-----------+-------+--------------------------------------------------------------+-----------+----------------+--------------------------------------------------------------------------------------------------------------------------------------+-------+------+---------+---------+---------+------+-----+-----------+-----+-------+--------+------+-------+-------+-------+-----+--------+---+-------+
    196|    242|     3|  881250949|    242|Kolya(1996)                                                   |24-Jan-1997|                |http://us.imdb.com/M/title-exact?Kolya%20(1996)                                                                                       |0      |0     |0        |0        |0        |1     |0    |0          |0    |0      |0       |0     |0      |0      |0      |0    |0       |0  |0      |
    186|    302|     3|  891717742|    302|L.A.Confidential(1997)                                        |01-Jan-1997|                |http://us.imdb.com/M/title-exact?L%2EA%2E+Confidential+(1997)                                                                         |0      |0     |0        |0        |0        |0     |1    |0          |0    |0      |1       |0     |0      |1      |0      |0    |1       |0  |0      |
     22|    377|     1|  878887116|    377|Heavyweights(1994)                                            |01-Jan-1994|                |http://us.imdb.com/M/title-exact?Heavyweights%20(1994)                                                                                |0      |0     |0        |0        |1        |1     |0    |0          |0    |0      |0       |0     |0      |0      |0      |0    |0       |0  |0      |
    244|     51|     2|  880606923|     51|LegendsoftheFall(1994)                                        |01-Jan-1994|                |http://us.imdb.com/M/title-exact?Legends%20of%20the%20Fall%20(1994)                                                                   |0      |0     |0        |0        |0        |0     |0    |0          |1    |0      |0       |0     |0      |0      |1      |0    |0       |1  |1      |
    166|    346|     1|  886397596|    346|JackieBrown(1997)                                             |01-Jan-1997|                |http://us.imdb.com/M/title-exact?imdb-title-119396                                                                                    |0      |0     |0        |0        |0        |0     |1    |0          |1    |0      |0       |0     |0      |0      |0      |0    |0       |0  |0      |
    298|    474|     4|  884182806|    474|Dr.Strangeloveor:HowILearnedtoStopWorryingandLovetheBomb(1963)|01-Jan-1963|                |http://us.imdb.com/M/title-exact?Dr.%20Strangelove%20or:%20How%20I%20Learned%20to%20Stop%20Worrying%20and%20Love%20the%20Bomb%20(1963)|0      |0     |0        |0        |0        |0     |0    |0          |0    |0      |0       |0     |0      |0      |0      |1    |0       |1  |0      |
    115|    265|     2|  881171488|    265|HuntforRedOctober,The(1990)                                   |01-Jan-1990|                |http://us.imdb.com/M/title-exact?Hunt+for+Red+October%2C+The+(1990)                                                                   |0      |1     |0        |0        |0        |0     |0    |0          |0    |0      |0       |0     |0      |0      |0      |0    |1       |0  |0      |
    253|    465|     5|  891628467|    465|JungleBook,The(1994)                                          |01-Jan-1994|                |http://us.imdb.com/M/title-exact?Jungle%20Book,%20The%20(1994)                                                                        |0      |0     |1        |0        |1        |0     |0    |0          |0    |0      |0       |0     |0      |0      |1      |0    |0       |0  |0      |
    305|    451|     3|  886324817|    451|Grease(1978)                                                  |01-Jan-1978|                |http://us.imdb.com/M/title-exact?Grease%20(1978)                                                                                      |0      |0     |0        |0        |0        |1     |0    |0          |0    |0      |0       |0     |1      |0      |1      |0    |0       |0  |0      |
      6|     86|     3|  883603013|     86|RemainsoftheDay,The(1993)                                     |01-Jan-1993|                |http://us.imdb.com/M/title-exact?Remains%20of%20the%20Day,%20The%20(1993)                                                             |0      |0     |0        |0        |0        |0     |0    |0          |1    |0      |0       |0     |0      |0      |0      |0    |0       |0  |0      |
```

## Losing any rows after join?
```
select COUNT(*) from 
ratings r 
join movies m on r.item_id = m.movieid;
```

- Output 
```
count |
------+
100000|
```


## Inner join of three table
```
select * from 
ratings r 
join movies m on r.item_id = m.movieid
join users u on r.user_id = u.user_id
limit 10;
```


## Columns with same name
```
select user_id from 
ratings r 
join movies m on r.item_id = m.movieid
join users u on r.user_id = u.user_id
limit 10;
```

- Output
```
SQL Error [42702]: ERROR: column reference "user_id" is ambiguous
  Position: 8
``` 

- Solution
```
select r.user_id, u.user_id from 
ratings r 
join movies m on r.item_id = m.movieid
join users u on r.user_id = u.user_id
limit 10;
```

- Output
```
user_id|user_id|
-------+-------+
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
      1|      1|
```

