### The MSR Custom image `msrfintech/keycloak`
We have a [custom image on dockerhub](https://hub.docker.com/repository/docker/msrfintech/keycloak/general) based on `jboss/keycloak:14.0.0` with our own SSL keys. You can use it with a `postgres` database also running on docker

To run it on docker, first create a user deifned `bridge` network if not already available and connect the below containers to the same network. Once connected to the same user-defined network, they can communicate with each other using their container names. Refer the [docker docs on networking](https://docs.docker.com/network/) for more details.

```
docker network list
docker network create msr

docker run --detach --name postgres --network msr -e POSTGRES_DB=keycloak -e POSTGRES_USER=keycloak -e POSTGRES_PASSWORD=password postgres:16

docker run --detach --publish 8443:8443 --name msrkeycloak --network msr -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin -e DB_VENDOR=postgres -e DB_ADDR=postgres -e DB_USER=keycloak -e DB_PASSWORD=password -e JDBC_PARAMS='connectTimeout=30' msrfintech/keycloak
```

## postgres
For more details on docker `postgres` refer the links belwo
- [Official postgres image](https://hub.docker.com/_/postgres)
- [How to guide](https://www.docker.com/blog/how-to-use-the-postgres-docker-official-image)

## keycloak
[Official documentation link](https://www.keycloak.org/documentation)
