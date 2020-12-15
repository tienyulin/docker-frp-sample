FROM alpine:latest

COPY /usr/bin/frp/ ./frpc/frpc
COPY /usr/bin/frp/ ./frpc/frpc.ini

ENTRYPOINT /usr/bin/frp/frpc -c /usr/bin/frp/frpc.ini
