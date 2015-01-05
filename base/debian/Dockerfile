FROM debian:latest
MAINTAINER Miran Hojnik <docker@3dot.net>
ADD etc /etc
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y ca-certificates inotify-tools nano pwgen supervisor unrar unzip wget
RUN apt-get clean
RUN mkdir /config /data
RUN useradd -u 500 core
ADD config /config
ADD loop /config/loop
RUN chmod +x /config/loop
CMD /config/loop
