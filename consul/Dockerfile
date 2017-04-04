FROM ubuntu:16.04
MAINTAINER Uday Bhanu Prasad <uday1bhanu@gmail.com>
ENV REFRESHED_AT 2017-04-03

RUN apt-get -qyy update; apt-get -qyy install curl unzip

ADD https://releases.hashicorp.com/consul/0.6.4/consul_0.6.4_linux_amd64.zip /tmp/consul.zip
RUN cd /usr/sbin; unzip /tmp/consul.zip; chmod +x /usr/sbin/consul; rm /tmp/consul.zip

RUN mkdir -p /webui/
ADD https://releases.hashicorp.com/consul/0.6.4/consul_0.6.4_web_ui.zip /webui/webui.zip

RUN cd /webui; unzip webui.zip; rm webui.zip;

ADD consul.json /config/

EXPOSE 53/udp 8300 8301 8301/udp 8302 8302/udp 8400 8500

VOLUME ["/data"]

ENTRYPOINT [ "/usr/sbin/consul", "agent", "-config-dir=/config" ]

CMD []
