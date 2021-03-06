# docker frp

frpc <br>
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/tienyu/frpc)

frps <br>
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/tienyu/frps)

frp is a fast reverse proxy to help expose a local server behind a NAT or firewall to the Internet. This demo packs frp setting into container for running easily.

## Build Image

Change directory to `docker-frp`.

### frpc

```bash=
docker build -t frpc -f frpc/Dockerfile .
```

### frps

```bash=
docker build -t frps -f frps/Dockerfile .
```

## Run Container

### frpc

Run this command on `Client`. You can replace `/etc/docker-frp/frpc` to any path you want, it means you mount this local path to `/usr/bin/frp/` in container.

```bash=
docker run -d --name=frpc --network=host -v /etc/docker-frp/frpc:/usr/bin/frp/ --restart=always tienyu/frpc
```

### frps

Run this command on `Server`. You can replace `/etc/docker-frp/frps` to any path you want, it means you mount this local path to `/usr/bin/frp/` in container.

```bash=
docker run -d --name=frps --network=host -v /etc/docker-frp/frps:/usr/bin/frp/ --restart=always tienyu/frps
```

## Edit frp setting

Both frpc and frps have to set `ini` setting file under `/usr/bin/frp/` folder in container, but we had mounted this folder to local, so you only need to copy `frpc.ini` file with `frpc` file or `frps.ini` file with `frps` file to your local path. More detail setting can refer to [frpc_full.ini](https://github.com/tienyulin/docker-frp-sample/blob/master/frpc/frpc_full.ini) and [frps_full.ini](https://github.com/tienyulin/docker-frp-sample/blob/master/frps/frps_full.ini).

* Default frpc.ini : Replace your server ip to server_addr

```txt=
[common]
server_addr = <server ip>
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

```txt=
[common]
bind_port = 7000

# setting http port, if port 80 is occupied, set another port here. 
vhost_http_port = 8081

# frps monitor dashboard
dashboard_port = 7500
dashboard_user = admin
dashboard_pwd = admin
```

### Check Permission

`frpc` and `frps` files must be executable, so make sure to give them permission.

```bash=
chmod 755 docker-frp/frpc/frpc
chmod 755 docker-frp/frps/frps
```

### Restart Container

After editing the `ini` file, remember to restart the container.

## Expose port

Remember to expose the port on the server which set in `frpc.ini` for application to use. For example, expose port `6000` on `server` for default setting of `ssh`.

## Connect through ssh by default setting

frps listens to port `6000` for frpc port `22` by default, which means the request will be passed to port `22` on `client` when connect to `server` on port `6000` through ssh.

```bash=
ssh <client user>@<server ip> -p 6000
```

## Reference

[1] [fatedier/frp](https://github.com/fatedier/frp)
