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
### Useful Docker Commands
```
docker run
docker stop
docker rm (add -f to force)
docker ps
docker login
docker push {image name}
```

## Kubernetes

- Create `node_deploy.yml`
```
apiVersion: apps/v1

kind: Deployment # pod, service # replicaset #ASG


metadata:
  name: node
spec:
  selector:
    matchLabels:
      app: node
  replicas: 3 # how many pods we want
  template:
    metadata:
      labels:
        app: node
    spec:
      containers:
        - name: node
          image: conorsm/node-app:v1

          ports:
            - containerPort: 3000
          #env:
           # - name: DB_HOST
            # value: mongod://mongo:27017/posts

          imagePullPolicy: Always
```

### Kubernetes Commands
```
kubectl
kubectl get service
kubectl create -f {name_of_yml_file}
kubectl get deploy
kubectl get pods
kubectl delete pod {node-name}
kubectl delete deploy {deploy_name}
```