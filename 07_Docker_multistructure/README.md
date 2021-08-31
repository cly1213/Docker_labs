# Docker support multi structure(ARM, x86)

Docker in the Linux environment needs to install [buildx](https://github.com/docker/buildx)

https://docs.docker.com/buildx/working-with-buildx/

```
docker login

docker buildx create --name mybuilder --use

docker buildx build --push --platform linux/arm/v7,linux/arm64/v8,linux/amd64 -t your_image .
```

Ref:

https://github.com/docker-library/official-images/tree/master/library

https://docs.docker.com/engine/reference/commandline/manifest/
