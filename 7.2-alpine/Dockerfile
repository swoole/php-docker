FROM php:7.2-alpine

MAINTAINER twosee <twose@qq.com>

# system tools
RUN apk update && \
    apk add --no-cache \
    curl \
    wget \
    zip \
    unzip \
    git \
    vim

# dependences
RUN apk add --no-cache \
    autoconf \
    dpkg-dev \
    dpkg \
    file \
    g++ \
    gcc \
    libstdc++ \
    libc-dev \
    make \
    pkgconf \
    re2c \
    pcre-dev \
    zlib-dev \
    libaio-dev \
    openssl \
    openssl-dev \
    hiredis

# extensions
RUN docker-php-ext-install \
    pdo_mysql \
    mysqli \
    json \
    opcache \
    sockets \
    pcntl && \
    echo "opcache.enable_cli=1" >> /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini && \
    pecl install redis && docker-php-ext-enable redis

# install composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    composer self-update --clean-backups

# dev tools
RUN apk add --no-cache \
    gdb \
    valgrind
