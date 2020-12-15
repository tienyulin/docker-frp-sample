FROM alpine:latest

RUN cp ./frps /usr/bin/frp/ & cp ./frps.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frps -c /usr/bin/frp/frps.ini
