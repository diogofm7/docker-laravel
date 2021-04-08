ARG PHP_VERSION=7.4

FROM php:${PHP_VERSION}-fpm-alpine

RUN apk update \
                && apk add --no-cache util-linux \
                shadow \
                vim \
                git \
                zip \
                openssh \
                libbz2 \
                icu-dev \
                ldb-dev \
                libldap \
                libxml2-dev \
                libxslt-dev \
                libzip-dev \
                openldap-dev \
                bzip2-dev

RUN DEBIAN_FRONTEND=noninteractive apk update \
        && DEBIAN_FRONTEND=noninteractive apk add --no-cache \
          curl \
          git \
          zip unzip \
        && docker-php-ext-install \
          bcmath \
          bz2 \
          calendar \
          exif \
          intl \
          ldap \
          mysqli \
          opcache \
          pdo_mysql \
          soap \
          xsl \
          zip \
          sockets


RUN apk update && apk add --no-cache \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

#### INSTALL REDIS ####
RUN apk update && apk add --no-cache autoconf gcc make g++ zlib-dev
RUN pecl install -o -f redis \
        &&  rm -rf /tmp/pear \
        &&  docker-php-ext-enable redis

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php --install-dir=/usr/local/bin \
    && php -r "unlink('composer-setup.php');"

COPY php.ini /usr/local/etc/php/conf.d/php.ini

RUN mkdir /.composer && \
    chmod 777 /.composer

RUN ln -snf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime && echo America/Sao_Paulo > /etc/timezone

WORKDIR /var/www