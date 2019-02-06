FROM php:7.2-fpm

RUN apt-get update

# Utils
RUN apt-get install -y git zip unzip

# PHP APCu
RUN pecl install apcu-5.1.8
RUN docker-php-ext-enable apcu

# PHP Intl
RUN apt-get install -y libicu-dev
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

# PHP Extensions
RUN apt-get install -y zlib1g-dev
RUN docker-php-ext-install pcntl pdo_mysql zip

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

# Clean
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
