FROM alpine:latest

COPY /usr/bin/frp/ ./frps/frps
COPY /usr/bin/frp/ ./frps/frps.ini

ENTRYPOINT /usr/bin/frp/frps -c /usr/bin/frp/frps.ini
