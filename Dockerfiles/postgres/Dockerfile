# Dockerfile
FROM ubuntu
ARG S6_OVERLAY_VERSION=3.2.0.0


RUN apt-get update && apt-get install -y nginx xz-utils
RUN apt-get install -y openssh-client
RUN apt-get install -y openssh-server
RUN apt install -y postgresql postgresql-client
RUN service ssh start
RUN service postgresql start
RUN wait
RUN su - postgres

RUN echo "daemon off;" >> /etc/nginx/nginx.conf
CMD ["/usr/sbin/nginx"]

ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-noarch.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-noarch.tar.xz
ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-x86_64.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-x86_64.tar.xz
ENTRYPOINT ["/init"]