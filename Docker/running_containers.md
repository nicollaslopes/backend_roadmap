# Running Containers

There is another way to run Docker containers called Docker compose. Behind the scenes they do exactly the same thing but Docker compose allows you to specify all of your application configuration within a **yaml** file and it makes dealing with the container cycle much easier. Let's create a container using **mysql** and **phpmyadmin**. Now we can run the `docker compose up -d` to run our containers.

```yaml
# docker-compose.yml

version: '3'

services:
  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: my-app
      MYSQL_USER: user
      MYSQL_PASSWORD: password
    ports:
      - "3306:3306"
    volumes:
      - type: volume
        source: my_app_db_data
        target: /var/lib/mysql

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    restart: always
    links:
      - db
    environment:
      PMA_HOST: db
      PMA_PORT: 3306
      MYSQL_ROOT_PASSWORD: root
    ports:
      - "80:80"

volumes:
  my_app_db_data:
```

If we want to stop the containers we can use `docker compose down` command.

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