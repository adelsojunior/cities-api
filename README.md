Cities API
Requirements
Linux
Git
Java 8
Docker
IntelliJ Community
Heroku CLI
DataBase
Postgres
Postgres Docker Hub
docker run --name cities-db -d -p 5432:5432 -e POSTGRES_USER=postgres_user_city -e POSTGRES_PASSWORD=super_password -e POSTGRES_DB=cities postgres
Populate
data
cd ~/workspace/sql-paises-estados-cidades/PostgreSQL

docker run -it --rm --net=host -v $PWD:/tmp postgres /bin/bash

psql -h localhost -U postgres_user_city cities -f /tmp/pais.sql
psql -h localhost -U postgres_user_city cities -f /tmp/estado.sql
psql -h localhost -U postgres_user_city cities -f /tmp/cidade.sql

psql -h localhost -U postgres_user_city cities

CREATE EXTENSION cube; 
CREATE EXTENSION earthdistance;
Postgres Earth distance
earthdistance--1.0--1.1.sql
OPERATOR <@>
postgrescheatsheet
datatype-geometric
Access
docker exec -it cities-db /bin/bash

psql -U postgres_user_city cities
Query Earth Distance
Point

select ((select lat_lon from cidade where id = 4929) <@> (select lat_lon from cidade where id=5254)) as distance;
Cube

select earth_distance(
    ll_to_earth(-21.95840072631836,-47.98820114135742), 
    ll_to_earth(-22.01740074157715,-47.88600158691406)
) as distance;
Spring Boot
https://start.spring.io/

Java 8

Gradle Project

Jar

Spring Web

Spring Data JPA

PostgreSQL Driver

Spring Data
jpa.query-methods
Properties
appendix-application-properties
jdbc-database-connectio
Types
JsonTypes
UserType
