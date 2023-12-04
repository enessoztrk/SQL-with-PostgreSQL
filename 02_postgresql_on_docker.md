# PostgreSQL on Docker

## 1. Status of Docker
`  sudo systemctl status docker ` 
- Must be running

## 2. Dockerhub
- Go to dockerhub 
- Serach for postgresql
- Click official image

## 3. Create postgresql container
```
docker run --rm -d \
    --name postgresql \
    -e POSTGRES_USER=postgres \
    -e POSTGRES_PASSWORD=Ankara06 \
    -e PGDATA=/var/lib/postgresql/data/pgdata \
    -p 5433:5432 \
    -v postgresql13_v:/var/lib/postgresql/data \
    postgres:13
```

## 4. Check status of container
```
docker ps


CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                                       NAMES
abdeec35557e   postgres:13   "docker-entrypoint.s…"   6 seconds ago   Up 5 seconds   0.0.0.0:5433->5432/tcp, :::5433->5432/tcp   postgresql
```

## 5. Connect psql
```
 docker exec -it postgresql psql -d postgres -U postgres
```
## 6. Create database, user and give privileges
```
create database traindb;
create user train with encrypted password 'Ankara06';
grant all privileges on database traindb to train;
```

## 7. Port forwarding
- On Virtualbox forward ports


## 8. DBeaver Connection
- Open DBeaver on your host machine
- Create a connection  

![Create new connection for new db](dbeaver_connection_for_new_db.png 'Create new connection for new db')

- Password Ankara06
- Test and finish.


