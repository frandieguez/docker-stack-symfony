FROM php:fpm

# zlibssl-dev required by mongodb
# lib1g-dev libicu-dev required by intl
# libmcrypt-dev required by mcrypt
# libmemcached-dev required by memcached
RUN apt-get update && \
    apt-get install -y libssl-dev zlib1g-dev libicu-dev g++ libmcrypt-dev libmemcached-dev && \
    docker-php-ext-enable opcache && \
    docker-php-source extract && \
    docker-php-ext-install intl && docker-php-ext-enable intl && \
    docker-php-ext-install bcmath && docker-php-ext-enable bcmath && \
    docker-php-ext-install zip && docker-php-ext-enable zip && \
    docker-php-ext-install pdo_mysql && docker-php-ext-enable pdo_mysql && \
    pecl install mcrypt-1.0.1 && docker-php-ext-enable mcrypt && \
    pecl install xdebug && docker-php-ext-enable xdebug && \
    pecl install mongodb && docker-php-ext-enable mongodb && \
    pecl install redis && docker-php-ext-enable redis && \
    pecl install memcached && docker-php-ext-enable memcached && \
    apt-get purge -y g++ && docker-php-source delete && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

