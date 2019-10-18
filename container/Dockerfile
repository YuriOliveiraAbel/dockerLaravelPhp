FROM php:7.2-apache
ENV TERM=xterm
WORKDIR /var/www/app

RUN apt-get update && \
    apt-get install -y \
    zlib1g-dev \
    libxml2-dev \
    nano \
    cron \
    libpng-dev \
    libpq-dev \
    curl \
    wkhtmltopdf \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    rsync && \
    apt-get clean -y

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN echo 'ServerName localhost' >> /etc/apache2/apache2.conf && \
    a2enmod rewrite

RUN docker-php-ext-install pdo_pgsql pgsql soap zip

RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini

RUN chmod 777 -R /var/www