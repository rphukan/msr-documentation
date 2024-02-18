### The MongoDB Inc community version : `docker pull mongodb/mongodb-community-server`
Here is the link to [docker hub](https://hub.docker.com/r/mongodb/mongodb-community-server) with a detailed installation instructions [here](https://www.mongodb.com/compatibility/docker)

Few points to note
- You will be able to connect to your MongoDB instance on mongodb://localhost:27017. You can try it with Compass, MongoDB’s GUI to visualize and analyze your data.
- Any data created as part of the lifecycle of that container will be destroyed once the container is deleted. You can do that with the Docker stop and rm commands. If you want to persist the data on your local machine, you can mount a volume using the -v argument.
- To initialize your MongoDB with a root user, you can use the environment variables MONGO_INITDB_ROOT_USERNAME and MONGO_INITDB_ROOT_PASSWORD. These environment variables will create a user with root permissions with the specified user name and password.
- We will be passing the Mongodb connection string like `mongodb+srv://username:password@clusterURL` as an environment variable to our application

```
docker run -d --name mongodb -p 27017:27017 -v C:\home\Projects\msr\data:/data/db -e MONGODB_INITDB_ROOT_USERNAME=admin -e MONGODB_INITDB_ROOT_PASSWORD=password mongodb/mongodb-community-server:7.0-ubi8
```

To manage your MongoDB server or to access, import, and export your data, you can use a second MongoDB container from which you will run the necessary CLI tools. To open up a Mongo Shell session to your MongoDB Atlas server, use mongosh and specify the cluster URL.

```
docker run -it \
--name mongosh mongodb/mongodb-community-server:7.0-ubi8 mongosh "mongodb://username:password@clusterURL/database"
```

### The Open Source version : `docker pull mongo`
Here is the link to the [docker hub](https://hub.docker.com/_/mongo)

- The environment variables MONGO_INITDB_ROOT_USERNAME and MONGO_INITDB_ROOT_PASSWORD are used to create a new user and set that user's password. This user is created in the admin authentication database and given the role of root, which is a "superuser" role.
- The -v /my/own/datadir:/data/db part of the command mounts the /my/own/datadir directory from the underlying host system as /data/db inside the container, where MongoDB by default will write its data files.

```
docker run -d --name mongodb \
	-v /my/own/datadir:/data/db \
	-e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
	-e MONGO_INITDB_ROOT_PASSWORD=secret \
	mongo:tag
```

The following example starts another MongoDB container instance and runs the mongosh (use mongo with 4.x versions) command line client against the original MongoDB container from the example above, allowing you to execute MongoDB statements against your database instance:

```
docker run -it --network some-network --rm mongo mongosh --host some-mongo test
```

### Some usefull docker commands
The docker exec command allows you to run commands inside a Docker container. The following command line will give you a bash shell inside your mongo container:
```
docker exec -it mongodb bash
```
The MongoDB Server log is available through Docker's container log:
```
docker logs mongodb
```
 
