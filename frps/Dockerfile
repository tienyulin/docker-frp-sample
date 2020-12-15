FROM alpine:latest

RUN cp ./frps/frps /usr/bin/frp/ & cp ./frps/frps.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frps -c /usr/bin/frp/frps.ini
