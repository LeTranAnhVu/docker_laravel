# COMMAND

#### NETWORK
- create network
```
 docker network create demo_nw
```


#### PHP
- create php-fpm images
```
 docker build -t i-php ./docker/php  
```
- run php-fpm container
```
 docker run -d --name c-php -v "$PWD":/home/www/mysite --network demo_nw i-php
```

#### HTTPD
- run httpd container
    - port 8080
    - mount configure file to container
```
 docker run -d --name c-httpd -v "$PWD":/home/www/mysite -v "$PWD"/docker/httpd/httpd.conf:/usr/local/apache2/conf/httpd.conf -p 8080:80 --network demo_nw httpd
```

#### MYSQL
- run mysql container
    - set env
    - MYSQL_ROOT_PASSWORD = password
    - MYSQL_DATABASE = docker_demo
```
 docker run -d --name c-mysql -v "$PWD"/db_stg:/var/lib/mysql -p 3306:3306 --network demo_nw -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=docker_demo mysql:5.7
```
