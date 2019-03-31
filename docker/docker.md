# Docker

## docker intro
- what is docker ?  
  docker is software container platform.
- what is container ?  
  - using containers, everything required to make a piece of software run is packaged into isolated containers.
  - containers can share a single kernel, and the only information that needs to be in a container image is the executable and its package dependencies, which never need to be installed on the host system.
  - virtual machines run guest operating systems. This is resource intensive, and the resulting disk image and application state is an entanglement of OS settings, system-installed dependencies, OS security patches, and other easy-to-lose, hard-to-replicate ephemera.

## getting started with docker
- containers
  - Dockerfile will define what goes on in the environment inside your container (also referred as image). create save and deploy images
- services
  - in a distributed application, different pieces of the app are called “services”.
a service only runs one image. scaling a service changes the number of container instances running that piece of software, assigning more computing resources to service in process.
    to define, run, and scale services with the Docker platform – just write a docker-compose.yml file.
- swarm
  - multi-container, multi-machine applications are made possible by joining multiple machines into a “Dockerized” cluster called a swarm. swarm is a group of machines that are running Docker and joined into a cluster.
- stack
  - a stack is a group of interrelated services that share dependencies, and can be orchestrated and scaled together. (java web app + monogdb).

## refs
  + https://github.com/docker/labs/tree/master/developer-tools/java/
  + https://www.youtube.com/watch?v=nqeqmVVOlrY


## docker commands
  + help  
    docker help
  + command help  
    docker <command> help
  + version  
    docker version
  + docker login  
    docker login -uyyyy -pxxxxx
  + search image  
    docker search busybox  // search the online Docker registry for a Image named busybox
  + list images  
    docker images
  + build image  
    docker build -t shippingdocker/nginx:1.0 -t shippingdocker/nginx:latest .
  + push image  
    docker push <image>:<tag>
  + pull image  
    docker pull <image>:<tag>
  + remove images  
    docker rmi <image id>
  + spin container and run image  
    docker run -t -i busybox:1.0  // create busybox 1.0 version; attach tty input; interactive
  + list running containers  
    docker ps
  + list all containers  
    docker ps --all
  + start container  
    docker start <container-id>
  + stop container  
    docker stop <container id>
  + remove container  
    docker rm <container id>
  + ssh into docker container  
    docker exec -it <hash> bash
    http://phase2.github.io/devtools/common-tasks/ssh-into-a-container/
  + run docker compose  
    docker-compose up -d       // detach mode i.e. in background
  + stop docker compose  
    docker-compose stop

## misc
  - stop all containers  
  docker kill $(docker ps -q)
  - remove all containers  
  docker rm -f $(docker ps -a -q)
  - remove all docker images  
  docker rmi -f $(docker images -q)
  - docker exec -ti <container-name-or-id> /bin/bash

## other tips
  + From inside of a Docker container, how do I connect to the localhost of the machine?
    - https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach

## docker image creation links
  + nginx image
    - https://serversforhackers.com/c/dckr-nginx-image
    - https://docs.docker.com/samples/library/nginx/