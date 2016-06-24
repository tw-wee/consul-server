FROM debian:jessie 
MAINTAINER kolyjjj@foxmail.com
RUN apt-get update \
&& apt-get install -y unzip \
&& rm -rf /var/lib/apt/lists/*
ADD https://releases.hashicorp.com/consul/0.6.4/consul_0.6.4_linux_amd64.zip /tmp/consul/consul.zip
RUN cd /bin && unzip /tmp/consul/consul.zip && chmod +x /bin/consul && rm /tmp/consul/consul.zip && mkdir -p /consul/config
ADD https://releases.hashicorp.com/consul/0.6.4/consul_0.6.4_web_ui.zip /tmp/consul/webui.zip
RUN cd /tmp && unzip /tmp/consul/webui.zip -d /tmp/consul/webui && mkdir /ui && mv /tmp/consul/webui/* /ui && rm /tmp/consul/webui.zip
ENTRYPOINT ["consul", "agent", "-config-dir", "/consul/config/"]


