FROM php:7-fpm

MAINTAINER "Ghazanfar Mir" <GhazanfarMir@gmail.com>

COPY composer-installer.sh /usr/local/bin/composer-installer

RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
        #====mcrypt====
        autoconf \
        libc-dev \
        pkg-config \
		libmcrypt-dev \
        #==================
		libpng-dev \
		ca-certificates \
		curl \
		xz-utils \
        sudo \
        cron \
        git \
        wget \
        libldb-dev \
        libldap2-dev \
        libsasl2-dev \
        python \
        vim \
        unzip \
        mysql-client \
        zip \
        libgeoip-dev \
        libpq-dev \
        libzip-dev \
        libbz2-dev \
        libgd2-dev \
        libjpeg-dev \
        libgif-dev \
        libxml2-dev \
        apt-utils \
        supervisor \
        wget \
        && docker-php-ext-install -j$(nproc) pdo_mysql mysqli pgsql pdo_pgsql \
        && docker-php-ext-install -j$(nproc) exif hash gettext sockets ctype xml zip pcntl \
        && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/  \
        && docker-php-ext-install -j$(nproc) gd

RUN chmod +x /usr/local/bin/composer-installer \
    && sleep 1 \
    && composer-installer \
    && mv composer.phar /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer \
    && composer --version