#FROM golang:1.11.1-alpine
## Install some dependencies needed to build the project
#RUN \
#    echo '@edge http://dl-cdn.alpinelinux.org/alpine/edge/main' >> /etc/apk/repositories && \
#    echo '@edge http://dl-cdn.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories && \
#    echo '@edge http://dl-cdn.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories && \
#    apk --no-cache upgrade
#RUN apk add bash ca-certificates git gcc g++ libc-dev tree jq curl filebeat@edge
#WORKDIR /src/app
#COPY filebeat.yml .

FROM docker.elastic.co/beats/filebeat:6.5.4
COPY filebeat.yml /usr/share/filebeat/filebeat.yml
USER root
RUN chown root:filebeat /usr/share/filebeat/filebeat.yml
USER filebeat