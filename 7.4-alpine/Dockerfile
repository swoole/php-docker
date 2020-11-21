FROM php:7.4-alpine

MAINTAINER twosee <twose@qq.com>

RUN apk update

# common tools
RUN apk add --no-cache \
    bash \
    curl \
    wget \
    zip \
    unzip \
    git \
    vim \
    curl-dev

# dev tools
RUN apk add --no-cache \
    autoconf \
    automake \
    c-ares \
    c-ares-dev \
    dpkg \
    dpkg-dev \
    file \
    g++ \
    gcc \
    libgcc \
    libstdc++ \
    libtool \
    make \
    openssl \
    openssl-dev \
    pcre-dev \
    pkgconf \
    re2c \
    zlib \
    zlib-dev

# extensions
RUN docker-php-ext-install \
    pdo_mysql \
    mysqli \
    json \
    opcache \
    sockets \
    pcntl \
    curl && \
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
    strace \
    valgrind
