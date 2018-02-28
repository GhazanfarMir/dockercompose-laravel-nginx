FROM php:7-fpm

LABEL maintainer="GhazanfarMir@gmail.com"

RUN apt-get update && apt-get install -y --no-install-recommends \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
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
        && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
        && composer --version

EXPOSE 9000
CMD ["php-fpm"]