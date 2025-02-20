FROM ubuntu

ARG S6_OVERLAY_VERSION=3.2.0.0

RUN apt-get update && apt-get install -y git xz-utils python3 python3-pip
ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-noarch.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-noarch.tar.xz
ADD https://github.com/just-containers/s6-overlay/releases/download/v${S6_OVERLAY_VERSION}/s6-overlay-x86_64.tar.xz /tmp
RUN tar -C / -Jxpf /tmp/s6-overlay-x86_64.tar.xz

RUN git clone https://github.com/xeacottx/dvd_rental.git
WORKDIR dvd_rental
ENTRYPOINT ["/init"]
