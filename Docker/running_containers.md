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