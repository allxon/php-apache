FROM php:7.3.21-apache

RUN apt-get update &&\
    apt-get install -y libmcrypt-dev libpq-dev libpng-dev libxslt-dev &&\
    pecl install mcrypt-1.0.3 && docker-php-ext-enable mcrypt &&\
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm wddx xmlrpc xsl
RUN a2enmod expires headers rewrite
