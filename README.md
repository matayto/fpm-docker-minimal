# fpm-docker-minimal

Simple repository to manage Dockerfile and any related configurations for a minimal `fpm` docker image

## Building and running

```
docker build -t fpm-<type> .
docker run -it fpm-<type> /bin/sh
```

## Cleaning up

```
docker container list | grep <image_name>
docker container rm $(docker container ls -a | grep <image_name> | grep -v CONTAINER | awk '{print $1}')

# optionally, clean up image
docker image rmi <image_name>
```
