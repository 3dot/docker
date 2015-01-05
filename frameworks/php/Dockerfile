FROM 3dot/nginx:latest
MAINTAINER Miran Hojnik <docker@3dot.net>

#Ubuntu apt update
RUN apt-get update

#Install php5 from official repo (almost very up to date)
RUN apt-get install -y php5-cli php5-curl php5-fpm php5-gd php5-mcrypt php5-mysql php5-pgsql php5-sqlite

#Setup nginx
RUN rm -rf /etc/nginx/addon.d /etc/php5/fpm/pool.d
RUN mkdir -p /etc/nginx/addon.d /etc/php5/fpm/pool.d
ADD etc /etc

#Setup supervisor daemon
ADD supervisord.conf /etc/supervisor/conf.d/php-fpm.conf