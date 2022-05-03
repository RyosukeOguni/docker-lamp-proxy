FROM php:5.6-apache


RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libmcrypt-dev \
  && mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled

RUN /bin/sh -c a2enmod rewrite

COPY ./php.ini /usr/local/etc/php/php.ini

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install intl pdo_mysql zip bcmath sockets mysql pcntl shmop

RUN docker-php-ext-install mbstring && \
  docker-php-ext-enable mbstring
  
RUN docker-php-ext-install mysqli && \
  docker-php-ext-enable mysqli

RUN pecl install xdebug-2.5.5 && \
  docker-php-ext-enable xdebug
