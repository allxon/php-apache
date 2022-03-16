FROM php:8.0.16-apache

RUN apt-get update &&\
    apt-get install -y -qq libmcrypt-dev libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip argon2 

RUN pecl install mcrypt-1.0.4

RUN docker-php-ext-enable mcrypt &&\
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm xsl
RUN a2enmod expires headers rewrite
