# Simple Python Flask Dockerized Application

Basic Python Flask app in Docker which prints the specific contents.

## Requirements

- [Install docker](https://docs.docker.com/engine/install/)
- [Install docker-compose](https://docs.docker.com/compose/install/)

## Prerequisites

1. Python Flask application code - app.py
2. Modules required for the application in file - requirements.txt

## Building the docker Image

1. For deploying the python flask app, we will be building a custom image using a Dockerfile.
```
FROM alpine:3.8  #-------Base image-------#

RUN mkdir /var/appdir/ #-------execute the cmd-------#

WORKDIR /var/appdir/  #-------Setting working directory for instructions in Dockerfile-------#

COPY . .  #-------copying contents to working directory-------#

EXPOSE 5000

RUN apk update && apk add --no-cache python3

RUN pip3 install -r requirements.txt

CMD ["/usr/bin/python3","app.py"]  #-------cmd to run when the container starts-------#

```
2. Run the Dockerfile
```
docker build -t freedafrancis/flask-app:1 .
```
3. You can give the required tags to the docker image
```
docker tag freedafrancis/flask-app:1 freedafrancis/flask-app:latest
```
4. Push the image to the repository
```
docker image push freedafrancis/flask-app:1
docker image push freedafrancis/flask-app:latest
```
Now, the image is available in the docker repository.

## Download precreated image

You can also just download the existing image from DockerHub.
```
docker image pull freedafrancis/flask-app:latest
```

## Run the container

Either you can run the container using the docker command 
```
docker container run --name flaskapp -d -p 80:5000 freedafrancis/flask-app
```
Or create a docker-compose file(docker-compose.yml) and use compose commands to start the container.
```
docker-compose up -d
 ```
 
## Provisioning
1. Clone this repository
```
git clone https://github.com/Freeda-F/python-flask-docker.git
```
2. Switch to the cloned directory
```
cd python-flask-docker
```
3. Start the docker containers using
```
docker-compose up -d
```
4. To stop and remove the containers,networks or volumes associated with this docker, you can use
```
docker-compose down -v
```
 
## Result

![image](https://user-images.githubusercontent.com/93197553/146643939-6d5ef5d6-08e2-4468-9bd8-beefe7823581.png)

