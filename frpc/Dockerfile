FROM alpine:latest
EXPOSE 80/tcp
EXPOSE 443/tcp

WORKDIR /usr/bin/frp
COPY frpc/frpc .
COPY frpc/frpc.ini .

ENV server_addr = 127.0.0.1

ENTRYPOINT /usr/bin/frp/frpc -c /usr/bin/frp/frpc.ini
