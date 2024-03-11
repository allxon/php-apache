FROM php:7.4.26-apache

RUN apt-get update &&\
    apt-get install -y libmcrypt-dev libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip vim &&\
    pecl install mcrypt-1.0.4 && docker-php-ext-enable mcrypt &&\
    apt-get clean &&\
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm xmlrpc xsl
RUN a2enmod expires headers rewrite
