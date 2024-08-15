FROM php:8.2-apache AS app_php
RUN a2enmod rewrite headers

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libcurl4-openssl-dev \
        libzip-dev \
        zip \
        zlib1g-dev \
        libicu-dev \
<<<<<<< HEAD
        libpq-dev \
        g++ \
        git \
    && docker-php-ext-configure intl \
    && docker-php-ext-install iconv pgsql pdo pdo_pgsql pgsql intl zip
=======
        g++ \
        git \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) iconv pdo pdo_mysql intl zip
>>>>>>> feat: docker conf

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

ENV PHP_IDE_CONFIG "serverName=dockerphp"

# Install composer
COPY --from=composer:2.3.4 /usr/bin/composer /usr/bin/composer
RUN mkdir /var/composer
ENV COMPOSER_HOME /var/composer
ENV COMPOSER_MEMORY_LIMIT -1
ENV COMPOSER_ALLOW_SUPERUSER 1
