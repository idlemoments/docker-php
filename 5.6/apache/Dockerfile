FROM php:5.6-apache

RUN echo "deb http://archive.debian.org/debian stretch main contrib non-free" > /etc/apt/sources.list


RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxml2-dev \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd exif \
    && docker-php-ext-install intl \
    && docker-php-ext-install opcache \
    && docker-php-ext-install zip \
    && docker-php-ext-install soap

RUN apt-get install -y git zlib1g-dev libmcrypt-dev nano vim --no-install-recommends \
    && apt-get clean \
    && docker-php-ext-install mcrypt zip \
    && a2enmod rewrite \
    && a2enmod ssl
