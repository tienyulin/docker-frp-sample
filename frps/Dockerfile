FROM alpine:latest
EXPOSE 80/tcp
EXPOSE 443/tcp

WORKDIR /usr/bin/frp
COPY frps/frps .
COPY frps/frps.ini .

ENTRYPOINT /usr/bin/frp/frps -c /usr/bin/frp/frps.ini
