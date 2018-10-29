FROM php:{{tag}}

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
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install \
    iconv \
    gd \
    pdo_mysql \
    mysqli \
    redis \
    iconv \
    mbstring \
    json \
    opcache \
    sockets \
    pcntl && \
    echo "opcache.enable_cli=1" >> /usr/local/etc/php/conf.d/docker-php-ext-opcache.ini

# install composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    composer self-update --clean-backups

# dev tools
RUN apk add --no-cache \
    gdb \
    valgrind
