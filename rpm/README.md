# fpm-docker-minimal

Simple repository to manage Dockerfile and any related configurations for a minimal `fpm` docker image

## Building and running

```
docker build -t fpm-rpm .
docker run -it fpm-rpm /bin/sh
```

## Testing an RPM build
```
mkdir build/tmp/test
mkdir -p build/tmp/test
mkdir -p build/tmp/test
echo 'testing' > build/tmp/test/testing.txt
fpm -s dir -t rpm -C ~/build --version 0.1.0 --iteration 1 --name testing .

rpm -qpl testing-0.1.0-1.x86_64.rpm
```

## Cleaning up

```
docker container list | grep fpm-rpm
docker container rm <container_id or name>

# optionally, clean up image
docker image rmi fpm-rpm
```
