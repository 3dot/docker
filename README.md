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
				
- **Sails.js**

	The Sails.js framework uses a very simple structure for deploying the app on /data.
	
		/data
			/app
				Here goes the sails.js project

**Instructions**  
Instructions will be here when I get around to writing them!

**Usage**  
The following commands can be used to deploy some of the services offered by the Docker containers in this repository.

- **Applications**

    - **phpMyAdmin**

            docker run --name="phpmyadmin" -d --link mysqlalias:mysqlcontainer --env=VIRTUAL_HOST=phpmyadmin.example.com 3dot/phpmyadmin
			# when linking mysqlcontainer is the name of the MySQL container you're linking to, while mysqlalias is the hostname alias available to the container as a reference to the external mysql container

    - **Wordpress**

            docker run --name="wordpress-data" 3dot/data
            docker run --name="wordpress" -it --link mysqlalias:mysqlcontainer --volumes-from="wordpress-data" --env=VIRTUAL_HOST=wordpress.example.com 3dot/wordpress

- **Base**

    - **Data**

            docker run --name="data" -it 3dot/data /bin/sh

    - **Debian**

            docker run --name="debian" -it 3dot/debian /bin/bash

    - **Ubuntu**

            docker run --name="ubuntu" -it 3dot/ubuntu /bin/bash

- **Frameworks**

    - **Nginx**

            docker run --name="nginx-data" 3dot/data
            docker run --name="nginx" -it --volumes-from="nginx-data" --env=VIRTUAL_HOST=example.com,www.example.com 3dot/nginx

    - **Nginx + PHP-FPM**

            docker run --name="nginx-php-data" 3dot/data
            docker run --name="nginx-php" -it --volumes-from="nginx-php-data" --env=VIRTUAL_HOST=example.com,www.example.com 3dot/php
	
	- **Node.js**

            docker run --name="node-data" 3dot/data
            docker run --name="node" -it --volumes-from="node-data" --env=VIRTUAL_HOST=example.com,www.example.com 3dot/node
	
	- **Sails.js**

            docker run --name="sails-data" 3dot/data
            docker run --name="sails" -it --volumes-from="sails-data" --env=VIRTUAL_HOST=example.com,www.example.com 3dot/sails

- **Services**

    - **HAProxy**

            docker run --name="haproxy-data" 3dot/data
            docker run --name="haproxy" -it --volumes-from="haproxy-data" -p 80:80 -p 443:443 3dot/haproxy
        
    - **HAProxy Config**

            docker run --name="haproxy-data" 3dot/data
            docker run --name="haproxy-config" -it --volumes-from="haproxy-data" -v /var/run/docker.sock:/var/run/docker.sock 3dot/haproxy-config

    - **PostgreSQL**

            docker run --name="postgresql-data" 3dot/data
            docker run --name="postgresql" -it --volumes-from="postgresql-data" 3dot/postgresql