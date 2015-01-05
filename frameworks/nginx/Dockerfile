FROM 3dot/ubuntu:latest
MAINTAINER Miran Hojnik <docker@3dot.net>

#Add nginx php key and repos
RUN wget -q http://nginx.org/packages/keys/nginx_signing.key -O- | apt-key add -
RUN echo "deb http://nginx.org/packages/ubuntu/ trusty nginx" >> /etc/apt/sources.list
RUN echo "deb-src http://nginx.org/packages/ubuntu/ trusty nginx" >> /etc/apt/sources.list

#Update ubuntu apt
RUN apt-get update

#Install nginx
RUN apt-get install -y nginx

#Configure nginx
RUN rm -rf /etc/nginx/*.d
RUN mkdir -p /etc/nginx/addon.d /etc/nginx/conf.d /etc/nginx/host.d /etc/nginx/nginx.d
ADD config /config
ADD etc /etc

#Setup supervisor deamon
ADD supervisord.conf /etc/supervisor/conf.d/nginx.conf

#expose container on port 80
EXPOSE 80