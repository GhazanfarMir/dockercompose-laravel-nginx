FROM php:7-fpm

MAINTAINER "Ghazanfar Mir" <GhazanfarMir@gmail.com>

COPY composer-installer.sh /usr/local/bin/composer-installer

RUN apt-get update && apt-get install -y --no-install-recommends \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
		ca-certificates \
		curl \
        wget \
        libldb-dev \
        python \
        vim \
        unzip \
        mysql-client \
        zip \
        libpq-dev \
        libgd2-dev \
        libjpeg-dev \
        libgif-dev \
        libxml2-dev \
        apt-utils \
        && docker-php-ext-install -j$(nproc) pdo_mysql mysqli pgsql pdo_pgsql \
        && docker-php-ext-install -j$(nproc) sockets pcntl \
        && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/  \
        && docker-php-ext-install -j$(nproc) gd \
        # Install Redis and xDebug
        && pecl install redis \
        && pecl install xdebug \
        && docker-php-ext-enable redis xdebug \
        ## Install Composer
        && chmod +x /usr/local/bin/composer-installer \
        && sleep 1 \
        && composer-installer \
        && mv composer.phar /usr/local/bin/composer \
        && chmod +x /usr/local/bin/composer \
        && composer --version