# Docker Demo App

## App Development with Docker Container

This repository includes a demo app that uses container technology for app development (Docker container). The demo app was set up using:

* Index html, JavaScript, and CSS as the frontend
* NodeJS with express module as the backend, and
* MongoDB as the data storage

The goal of the demo is to show how various app development tools can be containerized and run together using docker.

### Why Docker Container?
There are several reasons to use docker containers. One reason is that they are portable and can run on any system that supports the docker runtime. This means that you can develop and test your applications on your local machine and then deploy them to a production environment with minimal changes.

Another reason to use docker containers is that they are isolated from each other. This means that each container can run a different applications or services without affecting the others. This isolation also means that you can run multiple containers on the same host without them interfering with each other.

Lastly, docker containers are lightweight. This means that they use less resources than traditional virtual machines, making them ideal for running on servers with limited resources.

## Prerequisite
To use this repo, ensure you have the following set up on your local machine:

* Node.js and NPM. Learn how to install Node.js and NPM [Here](https://nodejs.org/en/download/). 
* Docker. Learn how to install docker [Here](https://docs.docker.com/desktop/install/windows-install/). 

## How to use the Project

There are two ways to use this project – **Docker and Docker compose**

### With Docker
* First, create docker network. Use the command below in the CLI
`sudo docker network create mongo-network`

* Start mongodb by running the command below
`sudo docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --network mongo-network mongo`

* Start mongo-express. Run the command below to start it
`sudo docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --network mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb -e ME_CONFIG_MONGODB_PORT=27017 mongo-express`

* Open mongo-express from your browser. Enter the address below
`http://localhost:8081`

* Create a database and collection in mongo-express. The database must be named **`my-db`**, and the collection must be named **`users`**. The collection should be created in the “my-db” database.

* Navigate to the app directory. While in the app directory, start the nodejs application. Run the following commands
`npm install` 
`node server.js`

* Access the nodejs application user interface from the server
`http://localhost:3000`

### With Docker Compose

* Start mongodb and mongo-express. To do this, run the command:
`docker-compose -f docker_compose_file.yaml up`

* Open mongo-express from your browser. Enter the address below
`http://localhost:8081`

* Create a database and collection in mongo-express. The database must be named **`my-db`**, and the collection must be named **`users`**. The collection should be created in the “my-db” database

* Navigate to the app directory. While in the app directory, start the nodejs application. Run the following commands
`npm install` 
`node server.js`

* Access the nodejs application user interface from the server
`http://localhost:3000`

## Build Docker Image from the Application

* Switch to the directory of this repo

* Run the command below

`docker build -t my-app:1.0 . `

The dot (.) at the end is the location of the Dockerfile



