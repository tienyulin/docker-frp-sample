FROM alpine:latest

COPY ./frps/frps /usr/bin/frp/
COPY ./frps/frps.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frps -c /usr/bin/frp/frps.ini
