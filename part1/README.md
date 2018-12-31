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