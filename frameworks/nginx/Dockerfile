FROM 3dot/ubuntu:latest
MAINTAINER Miran Hojnik <docker@3dot.net>
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ABF5BD827BD9BF62
RUN echo "deb http://nginx.org/packages/ubuntu/ trusty nginx" > /etc/apt/sources.list.d/nginx.list
RUN echo "deb-src http://nginx.org/packages/ubuntu/ trusty nginx" > /etc/apt/sources.list.d/nginx.list
RUN apt-get update
RUN apt-get install -y nginx
RUN rm -rf /etc/nginx/*.d
RUN mkdir -p /etc/nginx/addon.d /etc/nginx/conf.d /etc/nginx/host.d /etc/nginx/nginx.d
ADD config /config
ADD etc /etc
ADD supervisord.conf /etc/supervisor/conf.d/nginx.conf
EXPOSE 80
