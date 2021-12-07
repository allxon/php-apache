FROM arm64v8/php:5.6.40-apache

RUN apt-get update &&\
    apt-get install -y libmcrypt-dev libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip vim &&\
    docker-php-ext-configure mcrypt &&\
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-install calendar exif gd gettext mcrypt mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm wddx xmlrpc xsl
RUN a2enmod expires headers rewrite
