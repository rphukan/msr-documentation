### The Open Source version : `docker pull mongo`
Here is the link to the [docker hub](https://hub.docker.com/_/mongo)

```

```

### The MongoDB Inc community version : `docker pull mongodb/mongodb-community-server`
Here is the link to [docker hub](https://hub.docker.com/r/mongodb/mongodb-community-server)
with a detailed installation instructions [here](https://www.mongodb.com/compatibility/docker)

Few points to note
- You will be able to connect to your MongoDB instance on mongodb://localhost:27017. You can try it with Compass, MongoDB’s GUI to visualize and analyze your data.
- Any data created as part of the lifecycle of that container will be destroyed once the container is deleted. You can do that with the Docker stop and rm commands. If you want to persist the data on your local machine, you can mount a volume using the -v argument.
- To initialize your MongoDB with a root user, you can use the environment variables MONGO_INITDB_ROOT_USERNAME and MONGO_INITDB_ROOT_PASSWORD. These environment variables will create a user with root permissions with the specified user name and password.
- We will be passing the Mongodb connection string like `mongodb+srv://username:password@clusterURL` as an environment variable to our application
```
export MONGODB_VERSION=7.0-ubi8
docker run \n
--name mongodb -d \n
-p 27017:27017 \n
-v $(pwd)/data:/data/db \n
-e MONGO_INITDB_ROOT_USERNAME=user \n
-e MONGO_INITDB_ROOT_PASSWORD=pass \n
mongodb/mongodb-community-server:$MONGODB_VERSION
```

To manage your MongoDB server or to access, import, and export your data, you can use a second MongoDB container from which you will run the necessary CLI tools. To open up a Mongo Shell session to your MongoDB Atlas server, use mongosh and specify the cluster URL.

```
docker run -it --name mongosh mongodb/mongodb-community-server:$MONGODB_VERSION mongosh "mongodb://username:password@clusterURL/database"
```
