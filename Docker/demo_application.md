# Demo Application

Let's create a demo application using:

* React Front End
* Two API implementations:
	* node.js
	* golang
* PostgreSQL Database

```
// Makefile
DATABASE_URL:=postgres://postgres:foobarbaz@localhost:5432/postgres

.PHONY: run-postgres
run-postgres:
	@echo Starting postgres container
	-docker run \
		-e POSTGRES_PASSWORD=foobarbaz \
		-v pgdata:/var/lib/postgresql/data \
		-p 5432:5432 \
		postgres:15.1-alpine

.PHONY: run-api-node
run-api-node:
	@echo Starting node api
	cd api-node && \
		DATABASE_URL=${DATABASE_URL} \
		npm run dev

.PHONY: run-api-golang
run-api-golang:
	@echo Starting golang api
	cd api-golang && \
		DATABASE_URL=${DATABASE_URL} \
		go run main.go

.PHONY: run-client-react
run-client-react:
	@echo Starting react client
	cd client-react && \
		npm run dev
```

Now we can run postgresql running the command:

```shell
$ make run-postgres
```

We have now that database running in a container  

```shell
$ docker ps
```

Now we can run node-api running these commands:

```shell
$ nvm install 19.4
$ nvm use node 19.4
$ npm install
$ make run-api-node
```

Now we can run golang-api running these commands:

```shell
$ go mod download
$ make run-api-golang
```