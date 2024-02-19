## The MSR Custom image `msrfintech/keycloak`
We have a [custom image on dockerhub](https://hub.docker.com/repository/docker/msrfintech/keycloak/general) based on `jboss/keycloak:14.0.0` with our own SSL keys. You can use it with a `postgres` database also running on docker

```
docker network create keycloak-network

docker run -d \
--name postgres \
--net keycloak-network \
-e POSTGRES_DB=keycloak \
-e POSTGRES_USER=keycloak \
-e POSTGRES_PASSWORD=password \
postgres

docker run -p 8443:8443 --name msrkeycloak --net keycloak-network \
-e KEYCLOAK_USER=admin \
-e KEYCLOAK_PASSWORD=admin \
-e DB_VENDOR=postgres \
-e DB_ADDR=postgres \
-e DB_USER=keycloak \
-e DB_PASSWORD=password \
-e JDBC_PARAMS='connectTimeout=30' \
msrfintech/keycloak
```