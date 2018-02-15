FROM debian:jessie

MAINTAINER Loïs PUIG <lois.puig@kctus.fr> version: 0.1

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt-get update -qy && \
    apt-get install -qy \
            ca-certificates \
            curl

RUN apt-get install -qy \
			lksctp-tools && \
			curl -Lo /tmp/emqtt.deb http://emqtt.io/downloads/stable/debian8-deb && \
			dpkg -i /tmp/emqtt.deb

RUN apt-get autoremove -qy --purge \
            curl \
            && \
    apt-get clean -qy && \
    rm -rf /tmp/* \
           /var/lib/apt/lists/* \
           /var/tmp/*

EXPOSE 1883/tcp 8883/tcp 8083/tcp 8084/tcp 8080/tcp 18083/tcp

VOLUME ["/etc/emqttd/", "/var/lib/emqttd", "/var/log/emqttd/"]