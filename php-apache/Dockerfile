FROM php:7.3-apache

COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    unzip \
    libzip-dev \
    zlib1g-dev \
    && docker-php-ext-install \
    zip \
    pdo_mysql \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && a2enmod rewrite \
    && curl -sL https://deb.nodesource.com/setup_11.x | bash - \
    && apt-get install -y nodejs \
    && npm install npm@latest -g
COPY ./apache2.conf /etc/apache2/apache2.conf

WORKDIR /var/www/main_attendance
