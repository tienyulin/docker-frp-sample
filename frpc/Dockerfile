FROM alpine:latest

RUN cp ./frpc/frpc /usr/bin/frp/ & cp ./frpc/frpc.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frpc -c /usr/bin/frp/frpc.ini
