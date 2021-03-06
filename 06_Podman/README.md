# Podman
https://podman.io/

https://podman.io/getting-started/installation

```
podman search nginx

podman image pull docker.io/library/nginx

podman image ls

podman run -d -p 8080:80 docker.io/library/nginx

podman container ls

curl 127.0.0.1:8080

podman container stop ...

podman --help
```

## Docker vs Podman
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker_vs_podman.png"/>

```
ps -ef | grep docker
```

## Podman's pod
same as k8s's pod

```
podman pod create --name demo

podman pod ps

podman ps -a --pod

podman pod rm ...

#Create container inside one pod
podman container run -d --name test1 --pod demo docker.io/library/busybox 
```

## kubernetes stop support docker?
### Container Runtime
<img src="https://github.com/cly1213/Docker_labs/blob/main/img/container_runtime.png"/>

<img src="https://github.com/cly1213/Docker_labs/blob/main/img/docker_containerd.png"/>
