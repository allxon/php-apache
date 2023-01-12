FROM php:8.0.27-apache

RUN apt-get update &&\
    apt-get install -y -qq libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip argon2 libgmp-dev &&\
    pecl install apcu

RUN docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-enable apcu &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm xsl gmp
RUN a2enmod expires headers rewrite
