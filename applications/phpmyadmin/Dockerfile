FROM 3dot/php:latest
MAINTAINER Miran Hojnik <docker@3dot.net>

ENV VERSION 4.3.4
RUN mkdir -p /data/http

WORKDIR /data/http

RUN wget -O - "http://www.sourceforge.net/projects/phpmyadmin/files/phpMyAdmin/${VERSION}/phpMyAdmin-${VERSION}-all-languages.tar.gz/download" | tar --strip-components=1 -x -z
RUN rm -rf *.md .coveralls.yml ChangeLog composer.json config.sample.inc.php DCO doc examples phpunit.* README RELEASE-DATE-* setup
ADD data /data

ADD ./start.sh /start.sh
RUN chmod 755 /start.sh
CMD ["/bin/bash", "/start.sh"]