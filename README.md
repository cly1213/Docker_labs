# Docker_labs

## Docker

<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker.png"/>

nginx, busybox, flask, cron, MySQL, Redis

## Docker Compose

<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker-compose.png"/>

Good practice: Example Voting App

https://github.com/dockersamples/example-voting-app

## Docker Swarm

<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker-swarm.png"/>

### Deploy a stack to a swarm 
https://docs.docker.com/engine/swarm/stack-deploy/

1. docker-compose (single host): Development 
2. docker stack (swarm): Production

Example Voting App:

https://github.com/dockersamples/example-voting-app/blob/master/docker-stack.yml
```
docker stack deploy --compose-file docker-stack.yml vote
```
But K8s is a leader in the container orchestration field.

## Podman
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/podman.png"/>

Docker vs Podman
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker_vs_podman.png"/>
