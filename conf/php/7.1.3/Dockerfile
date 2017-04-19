FROM php:7.1.3-fpm-alpine
MAINTAINER yokotak0527 <mail@yokotakenji.me>

# 共通ユーザーの作成
ARG AGENT_UID=1000
RUN adduser -D -H -s /bin/sh -u ${AGENT_UID} dev

RUN \
    apk add --no-cache \
        curl-dev \
        libmcrypt-dev \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
        libxml2-dev \
        zlib-dev

RUN docker-php-ext-install \
    pdo_mysql \
    mysqli \
    mbstring \
    gd \
    exif \
    sockets \
    mcrypt

RUN mkdir -p /var/run/php-fpm
RUN chown dev:dev /var/run/php-fpm

COPY php.ini /usr/local/etc/php/
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
COPY zz-www.conf /usr/local/etc/php-fpm.d/zz-www.conf
COPY php-fpm.conf /usr/local/etc/php-fpm.conf
