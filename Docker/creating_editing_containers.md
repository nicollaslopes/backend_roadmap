# Creating and Editing containers

### Downloading images

To download an image, we can go to the the url https://hub.docker.com and search for the images we want. After that, we can run this command below to download an image. We can also check images that have been downloaded with the second command.

```
$ docker pull ubuntu
$ docker images
```

Once a image is downloaded, we can run this command.
``` 
$ docker run ubuntu
```

### Running a container

To get a bash and interact with the operation system inside a container, we can use this command below. The flag `-t` means that it will allocate a pseudo terminal and `-i` flag is the interaction mode. If we want to run a container and leave it running in the background, we can add the `-d` flag.

```
$ docker run -it ubuntu
```

### Checking containers

If we want to check which containers are running, we can use this command. We can also use`-a`flag to see containers with the "exited" status.

``` 
$ docker ps -a
```

### Running  an application in Container

If we want to run an application, we can use this command below.

```
$ docker exec -it <container-id> /bin/bash
```

Or we can execute a command this way.

```
$ docker exec -it <container-id> cat /etc/*release*
```

### Deleting and naming Containers

```
$ docker rm <container-id>                      // deleting a container
$ docker rmi <image-name>                       // deleting a image
$ docker run -dti --name <name> <image-name>    // naming a container
```

### Copying files to a Container

``` 
$ docker cp <file> <image-name or container-id>:<path>

// example
$ docker cp index.php d5421906a1f9:/
```

We can also copy a file inside a container to our host.

```  
$ docker cp <image-name or container-id>:<path-file> <new-file-name>

// example
$ docker cp d5421906a1f9:/index.php new-index.php
```

### Tag

When we use `docker pull` to download an image, the most up-to-date image is always downloaded, although we can use **tags** to download an image in a certain version. To do that, we need to use `:` and then insert the tag.

```
$ docker pull debian:9
```

### Creating a MySQL Container

Before start, we need to know that it's necessary to specify an environment variable  `MYSQL_ROOT_PASSWORD`. 

```
$ docker run -e MYSQL_ROOT_PASSWORD=<password> --name mysql -d -p 3306:3306 mysql
$ docker exec -it mysql bash
$ mysql -u root -p --protocol=tcp
```

### Setting up a storage

When we inspect a container, we can see a item called **Destination** which is a default directory inside the container where the database is stored. To configure the database to be saved outside a container, we need to redirect what is saved in that directory to another folder. 

```
$ docker inspect <image-name>

...
"Mounts": [
            {
                "Type": "volume",
                "Name": "6657573b8280db1e4501add35fe7df05d202c9648c5a0e28226f5f6e9e7a4c40",
                "Source": "/var/lib/docker/volumes/6657573b8280db1e4501add35fe7df05d202c9648c5a0e28226f5f6e9e7a4c40/_data",
                "Destination": "/var/lib/mysql",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
```

``` 
$ docker run -e MYSQL_ROOT_PASSWORD=<password> --name mysql -d -p 3306:3306 --volume=<directory-to-be-saved>:/var/lib/mysql mysql

// example

$ docker run -e MYSQL_ROOT_PASSWORD=<password> --name mysql -d -p 3306:3306 --volume=/home/user/mysql_data:/var/lib/mysql mysql
```

### Limiting memory and CPU

To see how much CPU and memory is being consumed in a container, just run the following command.

```
$ docker stats <container-id or image-name>

// limiting memory
$ docker update <container-id or image-name> -m 128M 

// or we can specify when the container is created
$ docker run --name <apelido-imagem> -dti -m 128M --cpus 0.2 ubuntu
```

### Information, logs and process

```
$ docker info

$ docker container logs <container-id or image-name>

$ docker container top <container-id or image-name>
```

### Network

We can also create a new Docker network and create a container that attaches to it.

```
$ docker network ls

NETWORK ID     NAME      DRIVER    SCOPE
023f40b5d390   bridge    bridge    local
7a9fc04162bd   host      host      local
cfb0245956f6   none      null      local

$ docker network create my-network
$ docker network ls

NETWORK ID     NAME         DRIVER    SCOPE
023f40b5d390   bridge       bridge    local
7a9fc04162bd   host         host      local
6b8a7332b7d4   my-network   bridge    local
cfb0245956f6   none         null      local

// attaching

$ docker run -d --network my-network ubuntu
$ docker ps -a

// checking the new network created
$ docker network inspect my-network

[
    {
        "Name": "my-network",
        "Id": "6b8a7332b7d42cef9323db9ef648181bb5a3c943a0bcecaaba19693f",
        "Created": "2025-01-08T09:45:58.665303937-03:00",
        "Scope": "local",
        "Driver": "bridge",
        
        ....
        "Containers": {
            "568690c500a35ea5a5484ed34cea8a6bac325f31f914062f0c8daf10": {
                "Name": "happy_shirley",
                "EndpointID": "a3426c8168461452ab28e86a1c3f44de333be37bbd54f1",
                "MacAddress": "02:42:ac:12:00:03",
                "IPv4Address": "172.18.0.3/16",
                "IPv6Address": ""
            },
            "9ee2e5a17edd0596277eef615d1fa1c694239a85082d159b19f466b98": {
                "Name": "festive_hellman",
                "EndpointID": "cfb612accaa89b5c7e79d423476aef3257fc884a651ea2",
                "MacAddress": "02:42:ac:12:00:02",
                "IPv4Address": "172.18.0.2/16",
                "IPv6Address": ""
            }
        },
        "Options": {},
        "Labels": {}
    }
]


$ docker container inspect 99630b9b105e | grep network

            "NetworkMode": "my-network",
                "my-network": {

```

Most Used Options

* -d
* --entrypoint
* --env, -e, --env-file
* --init
* --interactive, -I, -tty, -t
* --mount, --volume, -v
* --name
* --network, --net
* --platform
* --publish, -p
* --restart
* --rm