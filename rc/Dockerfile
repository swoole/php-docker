FROM php:rc

MAINTAINER twosee <twose@qq.com>

RUN apt-get update

RUN apt-get install -y \
    procps \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    openssl \
    libssh-dev \
    libpcre3 \
    libpcre3-dev \
    libonig-dev \
    curl \
    wget \
    zip \
    unzip \
    git \
    vim && \
    apt autoremove && \
    apt clean

RUN docker-php-ext-install \
    iconv \
    gd \
    pdo_mysql \
    mysqli \
    iconv \
    mbstring \
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

# dev-tools for master
RUN apt-get install -y gdb valgrind && \
    apt autoremove && apt clean
