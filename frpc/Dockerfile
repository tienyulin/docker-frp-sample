FROM alpine:latest

RUN ls
RUN cp frpc/frpc /usr/bin/frp/ 
RUN cp frpc/frpc.ini /usr/bin/frp/

ENTRYPOINT /usr/bin/frp/frpc -c /usr/bin/frp/frpc.ini
