**Source**
This repository is heavily sourced from https://github.com/maxexcloo/Docker and mostly altered for internal use.

**Description**
This repository contains a collection of Docker configurations I've put together to meet my needs.

**Directory Structure**

- **Nginx**

    Nginx based frameworks have a simple directory structure that can be used to easily deploy web applications using a volume on /data.

        /data
            /conf
                nginx-*.conf // included by nginx
                php-*.conf // included by php-fpm
            /http
                index.html // root web directory (index file is index.html or index.php)
            /logs
                nginx.log // nginx log file
                php-fpm.log // php-fpm log file
            /secure
                filename.ext // private files such as passwords or keys

**Instructions**  
Instructions will be here when I get around to writing them!

**Usage**  
The following commands can be used to deploy some of the services offered by the Docker containers in this repository.

- **Applications**

    - **phpMyAdmin**

            docker run --name="phpmyadmin" -d --link mariadb:mariadb --env=VIRTUAL_HOST=phpmyadmin.example.com maxexcloo/phpmyadmin

    - **Wordpress**

            docker run --name="wordpress-data" maxexcloo/data
            docker run --name="wordpress" -it --link mariadb:mariadb --volumes-from="wordpress-data" --env=VIRTUAL_HOST=wordpress.example.com maxexcloo/wordpress

- **Base**

    - **Data**

            docker run --name="data" -it maxexcloo/data /bin/sh

    - **Debian**

            docker run --name="debian" -it maxexcloo/debian /bin/bash

    - **Ubuntu**

            docker run --name="ubuntu" -it maxexcloo/ubuntu /bin/bash

- **Frameworks**

    - **Nginx**

            docker run --name="nginx-data" maxexcloo/data
            docker run --name="nginx" -it --volumes-from="nginx-data" --env=VIRTUAL_HOST=example.com,www.example.com maxexcloo/nginx

    - **Nginx + PHP-FPM**

            docker run --name="nginx-php-data" maxexcloo/data
            docker run --name="nginx-php" -it --volumes-from="nginx-php-data" --env=VIRTUAL_HOST=example.com,www.example.com maxexcloo/nginx-php

- **Services**

    - **HAProxy**

            docker run --name="haproxy-data" maxexcloo/data
            docker run --name="haproxy" -it --volumes-from="haproxy-data" -p 80:80 -p 443:443 maxexcloo/haproxy
        
    - **HAProxy Config**

            docker run --name="haproxy-data" maxexcloo/data
            docker run --name="haproxy-config" -it --volumes-from="haproxy-data" -v /var/run/docker.sock:/var/run/docker.sock maxexcloo/haproxy-config

    - **PostgreSQL**

            docker run --name="postgresql-data" maxexcloo/data
            docker run --name="postgresql" -it --volumes-from="postgresql-data" maxexcloo/postgresql