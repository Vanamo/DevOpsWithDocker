# Exercise 1.1

CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                          PORTS               NAMES
5a84b64bae80        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) 31 seconds ago                           stupefied_tesla
f8d45bb865ff        nginx               "nginx -g 'daemon of…"   About a minute ago   Exited (0) 25 seconds ago                           romantic_mclaren
4a7dd479d44c        nginx               "nginx -g 'daemon of…"   About a minute ago   Up About a minute               80/tcp              jovial_torvalds
f66072f04cba        nginx               "nginx -g 'daemon of…"   2 minutes ago        Exited (0) About a minute ago                       agitated_colden
18e280203977        nginx               "nginx -g 'daemon of…"   About an hour ago    Exited (0) About an hour ago                        upbeat_ride

# Exercise 1.2

vseppane@lx7-fuxi359:/home/local/vseppane/DevOpsWithDocker/part1$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
vseppane@lx7-fuxi359:/home/local/vseppane/DevOpsWithDocker/part1$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

# Exercise 1.3

docker run -d -it ubuntu:16.04 sh -c 'read website; sleep 3; curl http://$website;'

docker exec -it loving_leakey bash

install curl

docker attach loving_leakey

# Exercise 1.4

Dockerfile:

FROM ubuntu:16.04

WORKDIR /mydir
COPY skripti.sh .
RUN apt-get update && apt-get install -y curl
CMD ./skripti.sh

Commands:

docker build -t curler .
docker run -it curler

# Exercise 1.5

Dockerfile:

FROM ubuntu:16.04

WORKDIR /mydir
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt-get install -y nodejs
EXPOSE 5000
RUN npm install
CMD npm start

Commands:

docker build .
docker run -p 1234:5000 d5

# Exercise 1.6

Dockerfile:

FROM ubuntu:16.04

WORKDIR /mydir
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt-get install -y nodejs
RUN npm install
EXPOSE 8000
CMD npm start

Commands:

docker build -t backend .
docker run -p 8000:8000 -v $(pwd)/logs.txt:/mydir/logs.txt backend

# Exercise 1.7

Dockerfiles:

Frontend:

FROM ubuntu:16.04

WORKDIR /mydir
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt-get install -y nodejs
EXPOSE 5000
RUN npm install
ENV API_URL http://127.0.0.1:8000
CMD npm start

Backend:

FROM ubuntu:16.04

WORKDIR /mydir
COPY . .
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash && apt-get install -y nodejs
RUN npm install
EXPOSE 8000
ENV FRONT_URL http://localhost:5000
CMD npm start

Commands:

docker build -t backend .
docker run -p 8000:8000 -v $(pwd)/logs.txt:/mydir/logs.txt backend

docker build -t frontend .
docker run -p 5000:5000 frontend