FROM php:8.1.5-apache

RUN apt-get update &&\
    apt-get install -y -qq libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip argon2 &&\
    apt-get clean

RUN docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm xsl
RUN a2enmod expires headers rewrite remoteip
