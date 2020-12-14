# docker frp

## Build Image
Change directory to docker-frp.

### frpc
```
$ docker build -t frpc -f frpc/Dockerfile .
```

### frps
```
$ docker build -t frps -f frps/Dockerfile .
```

## Run Container

### frpc
Setting server_addr for frpc connecting to frps.
```
$ docker run --network=host -e server_addr=xxx.xxx.xxx.xxx frpc
```

### frps
```
$ docker run --network=host frps
```
