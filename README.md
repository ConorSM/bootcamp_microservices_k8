# Docker
When docker is installed test with 
```
docker run hello-world
```
To see images on local machine
```
docker images
```
## Build app on docker

- Build Dockerfile in app directory
```
# node as our base image
FROM node

# select home location inside our image/container
WORKDIR /usr/src/app

# copy required dependencies
COPY package*.json ./

# npm install
RUN npm install -g npm@7.20.6

# copy app folder
COPY . .

# 3000
EXPOSE 3000

# npm start - node app.js
CMD ["node", "app.js"]
```

- To run app
```
 docker run -d -p 80:3000 conorsm/node-app:v1
```
## Useful docker commands
```
docker run
docker stop
docker rm
docker ps
```