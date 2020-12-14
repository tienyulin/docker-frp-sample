# docker frp
frp is a fast reverse proxy to help expose a local server behind a NAT or firewall to the Internet.

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
$ docker run  -d --name=frpc --network=host -v /etc/docker-frp/frpc:/usr/bin/frp/ --restart=always frpc
```

### frps
Run this command on `Server`.
```
$ docker run  -d --name=frps --network=host -v /etc/docker-frp/frps:/usr/bin/frp/ --restart=always frps
```

## Edit frp setting
Both frpc and frps put `ini` setting file under `/usr/bin/frp/` in container. Edit `ini` file, then restart the container.

* Default frpc.ini
```
[common]
server_addr = $server_addr
server_port = 7000

# not exit when first login failed, keep relogining.
login_fail_exit = false 

[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22

# remote port listen by frps
remote_port = 6000
```

* Default frps.ini
```
[common]
bind_port = 7000

# setting http port, if port 80 is occupied, set another port here. 
vhost_http_port = 8081

# frps monitor dashboard
dashboard_port = 7500
dashboard_user = admin
dashboard_pwd = admin
```

## Expose port
Remember to expose the port on the server which set in `frpc.ini` for application to use. For example, expose port `6000` on `server` for default setting of `ssh`.

## Connect through ssh by default setting
frps listens to port `6000` for frpc port `22` by default, which means the request will be passed to port `22` on `client` when connect to `server` on port `6000` through ssh. 
```
$ ssh <client user>@<server ip> -p 6000
```

## Reference
[1] [fatedier/frp](https://github.com/fatedier/frp)
