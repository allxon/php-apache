FROM php:8.0.30-apache

RUN apt-get update &&\
    apt-get install -y -qq libpq-dev libpng-dev libxslt-dev cron jq logrotate unzip argon2 libgmp-dev libapache2-mod-security2 &&\
    pecl install apcu &&\
    apt-get clean

RUN mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf &&\
    rm -rf /etc/modsecurity/crs &&\
    curl -s -L https://github.com/coreruleset/coreruleset/archive/refs/tags/v4.0.0.tar.gz | tar -xz -C /usr/share/ &&\
    rm -rf /usr/share/modsecurity-crs &&\
    mv /usr/share/coreruleset-4.0.0 /usr/share/modsecurity-crs &&\
    mv /usr/share/modsecurity-crs/crs-setup.conf.example /usr/share/modsecurity-crs/crs-setup.conf &&\
    sed -i "s/IncludeOptional \/usr\/share\/modsecurity-crs.*/IncludeOptional \/usr\/share\/modsecurity-crs\/crs-setup.conf/" /etc/apache2/mods-available/security2.conf &&\
    sed -i 's/SecRuleEngine DetectionOnly/SecRuleEngine On/' /etc/modsecurity/modsecurity.conf &&\
    sed -i 's/SecResponseBodyAccess On/SecResponseBodyAccess Off/' /etc/modsecurity/modsecurity.conf &&\
    sed -i 's/SecAuditEngine RelevantOnly/SecAuditEngine Off/' /etc/modsecurity/modsecurity.conf &&\
    sed -i 's/SecStatusEngine On/SecStatusEngine Off/' /etc/modsecurity/modsecurity.conf

RUN docker-php-ext-configure mysqli --with-mysqli=mysqlnd &&\
    docker-php-ext-enable apcu &&\
    docker-php-ext-install calendar exif gd gettext mysqli opcache pcntl pgsql shmop soap sockets sysvmsg sysvsem sysvshm xsl gmp
RUN a2enmod expires headers rewrite
