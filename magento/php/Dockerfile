FROM php:7.4.12-fpm-buster

COPY sources.list /etc/apt
COPY magento.ini /usr/local/etc/php/conf.d
COPY composer.phar /usr/local/bin/composer

ENV username=c55018d4d8680c36bd35183e3be66aae password=3ce96aed3a088582bb81f73ab9f6bcf3

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libicu-dev \
    libxml2-dev \
    libxslt1-dev \
    libzip-dev \
    libjpeg-dev \
    libwebp-dev \
    composer \
    git \
    && docker-php-ext-configure gd --with-jpeg-dir=/usr/include --with-webp-dir=/usr/include --with-png-dir=/usr/include --with-freetype-dir=/usr/include \
    && docker-php-ext-install  gd \
    && docker-php-ext-configure bcmath \
    && docker-php-ext-install  bcmath \
    && docker-php-ext-configure intl \
    && docker-php-ext-install  intl \
    && docker-php-ext-configure pdo_mysql \
    && docker-php-ext-install  pdo_mysql \
    && docker-php-ext-configure soap \
    && docker-php-ext-install soap \
    && docker-php-ext-configure zip \
    && docker-php-ext-install  zip \
    && docker-php-ext-configure xsl \
    && docker-php-ext-install  xsl \
    && docker-php-ext-configure sockets \
    && docker-php-ext-install  sockets \
    && pecl install redis-5.3.2 \
    && docker-php-ext-enable redis \
    && mv $PHP_INI_DIR/php.ini-production $PHP_INI_DIR/php.ini \
    && chmod a+x /usr/local/bin/composer