# Building Container Images

Dockerfile is a text document that contains all the commands a user could call on the command line to assemble a image.

We can create a dockerfile like this and run `docker build -t api-node:0 .` command to build our container.

```dockerfile
# Dockerfile

FROM ubuntu

RUN apt update && apt install nodejs npm -y

COPY . .

RUN npm install

CMD ["npm", "run", "dev"]
```

``` 
$ docker image ls

REPOSITORY   TAG           IMAGE ID       CREATED          SIZE
api-node     0             6274cc67f6a5   3 minutes ago    986MB
<none>       <none>        c67704a5135a   26 minutes ago   218MB
<none>       <none>        de80a0e076be   27 minutes ago   123MB
postgres     15.1-alpine   f8428074961e   24 months ago    243MB
```


But there are so many ways to improve it.

We can use the official image and run this command: `docker build -t api-node:1 .`

*(Alpine is a Linux distribution. It's good for building docker images because it's quite small and it's also good from a security perspective to have fewer utilities and dependencies installed)*

If we have a node app and we want to ignore node_modules, we can create a file called `.dockerignore` and add `node_modules` in it or we can use `COPY ./src .` to copy only the `src` directory. A technique to execute as a non-root user is using `USER` and we can make sure that the files we're copying are owned by that node user using  `chown`.

```dockerfile
# Dockerfile

# Pin specific version for stability
FROM node:19.6-alpine

# Set NODE_ENV
ENV NODE_ENV production

# Specify working directory other than /
WORKDIR /usr/src/app

# Copy only files required to install
# dependencies (better layer caching)
COPY package*.json ./

# Install only production dependencies
RUN npm ci --only=production

# Use non-root user
# Use --chown on COPY commands to set file permissions
USER node

# Copy remaining source code AFTER installing dependencies.
# Again, copy only the necessary files
COPY --chown=node:node ./src .

# Indicate expected port
EXPOSE 3000

CMD ["node", "index.js"]
```

