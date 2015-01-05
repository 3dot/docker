FROM 3dot/nginx:latest
MAINTAINER Miran Hojnik <docker@3dot.net>
RUN apt-get update
RUN apt-get install -y php5-cli php5-curl php5-fpm php5-gd php5-mcrypt php5-mysql php5-pgsql php5-sqlite
RUN rm -rf /etc/nginx/addon.d /etc/php5/fpm/pool.d
RUN mkdir -p /etc/nginx/addon.d /etc/php5/fpm/pool.d
ADD etc /etc
ADD supervisord.conf /etc/supervisor/conf.d/php-fpm.conf