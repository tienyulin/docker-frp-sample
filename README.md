# docker frp

## Build Image
Change directory to `docker-frp`.

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
Run this command on `Client` and set `server_addr` for frpc connecting to frps.
```
$ docker run --network=host -e server_addr=xxx.xxx.xxx.xxx frpc
```

### frps
Run this command on `Server`.
```
$ docker run --network=host frps
```

## Edit frp setting
Both frpc and frps put `ini` setting file under `/usr/bin/frp/` in container. Edit `ini` file, then restart the container.
