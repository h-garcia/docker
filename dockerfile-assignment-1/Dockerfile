# Instructions from the app developer
# - you should use the 'node' official image, with the alpine 6.x branch
FROM node:6-alpine

# - this app listens on port 3000, but the container should launch on port 80
  #  so it will respond to http://localhost:80 on your computer
EXPOSE 3000

# - then it should use alpine package manager to install tini: 'apk add --update tini'
RUN apk add --update tini

# - then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# - Node uses a "package manager", so it needs to copy in package.json file
COPY package.json package.json

# - then it needs to run 'npm install' to install dependencies from that file
# - to keep it clean and small, run 'npm cache clean --force' after above
RUN npm install && npm cache clean

# - then it needs to copy in all files from current directory
COPY . /usr/src/app

#COPY . .
### This above means.. copy all in my current directory to current dir in the container

# - then it needs to start container with command '/sbin/tini -- node ./bin/www'
CMD ["tini", "--", "node", "./bin/www"]
