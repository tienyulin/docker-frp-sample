FROM alpine:latest

COPY ./frpc/frpc /usr/bin/frp/
COPY ./frpc/frpc.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frpc -c /usr/bin/frp/frpc.ini
