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