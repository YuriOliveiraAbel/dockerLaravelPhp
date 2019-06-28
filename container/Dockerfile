FROM php:7.3-apache

# ------------------------------------------------------------------------------
# Criar diretório
# ------------------------------------------------------------------------------
WORKDIR /var/www/app

# ------------------------------------------------------------------------------
# Instalação de pacotes
# ------------------------------------------------------------------------------

RUN apt-get update
RUN apt-get install -y zlib1g-dev \
   libxml2-dev \
   nano \
   cron \
   libpng-dev \
   libpq-dev \
   libc-client-dev \
   libkrb5-dev \
   wget \
   supervisor \
   git \
   gnupg \
   bzip2 \
   rsync && \
   apt-get clean -y

# ------------------------------------------------------------------------------
# Habilitação da extensão ZIP
# ------------------------------------------------------------------------------
# RUN pecl install zip && echo "extension=zip.so" > /usr/local/etc/php/conf.d/zip.ini

# ------------------------------------------------------------------------------
# Habilitação de extensões php
# ------------------------------------------------------------------------------
RUN docker-php-ext-install pdo_pgsql pgsql pdo_mysql mysqli

# ------------------------------------------------------------------------------
# Instalar o composer
# ------------------------------------------------------------------------------
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# ------------------------------------------------------------------------------
# ServerName para evitar erros, e habilitação de extensões do PHP
# ------------------------------------------------------------------------------
RUN echo 'ServerName localhost' >> /etc/apache2/apache2.conf && a2enmod rewrite ssl