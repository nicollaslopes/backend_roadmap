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