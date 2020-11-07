FROM php:7.4.10-cli-buster

COPY sources.list /etc/apt

RUN apt-get clean all && apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libxml2-dev \
    libxslt1-dev \
    libzip-dev \
    && apt-get autoremove \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-configure pdo_mysql \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure xsl \
    && docker-php-ext-install xsl \
    && docker-php-ext-configure soap \
    && docker-php-ext-install soap \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && docker-php-ext-configure sockets \
    && docker-php-ext-install sockets \
    && pecl install redis-5.3.2 \
    && docker-php-ext-enable redis