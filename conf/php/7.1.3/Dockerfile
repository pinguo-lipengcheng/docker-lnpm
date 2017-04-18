FROM php:7.1.3-fpm-alpine
MAINTAINER yokotak0527 <mail@yokotakenji.me>

# 共通ユーザーの作成
ARG AGENT_UID=1000
RUN adduser -D -H -s /bin/sh -u ${AGENT_UID} dev

# https://askubuntu.com/questions/788739/502-bad-gateway-nginx-php7-fpm
#RUN apk --no-cache add libpcre3

# setup php
#RUN apk --no-cache add \
#  curl-dev \
#  libmcrypt-dev \
#  freetype-dev \
#  libjpeg-turbo-dev \
#  libpng-dev \
#  libxml2-dev \
#  zlib-dev \
#  && NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1) \
#  && docker-php-ext-install -j${NPROC} \
#    curl \
#    dom \
#    mbstring \
#    mcrypt \
#    pdo \
#    pdo_mysql \
#    simplexml \
#    zip \
#  && docker-php-ext-configure gd \
#    --with-freetype-dir=/usr/include/ \
#    --with-jpeg-dir=/usr/include/ \
#    --with-png-dir=/usr/include/ \
#  && docker-php-ext-install -j${NPROC} gd

RUN mkdir -p /var/run/php-fpm
RUN chown dev:dev /var/run/php-fpm

COPY php.ini /usr/local/etc/php/
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
COPY zz-www.conf /usr/local/etc/php-fpm.d/zz-www.conf
COPY php-fpm.conf /usr/local/etc/php-fpm.conf
