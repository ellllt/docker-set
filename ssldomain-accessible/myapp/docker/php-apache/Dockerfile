FROM php:8.2-apache

RUN apt-get update \
   && apt-get install -y --no-install-recommends \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      libpng-dev \
      libmcrypt-dev \
      libicu-dev \
      libonig-dev \
      libzip-dev \
   && apt-get -y clean \
   && rm -rf /var/lib/apt/lists/* \
   && a2enmod rewrite headers \
   && docker-php-ext-install -j$(nproc) intl mbstring mysqli pdo_mysql opcache zip && docker-php-ext-enable mysqli \
   && pecl install xdebug \
   && docker-php-ext-enable xdebug

COPY ./php/php.ini /usr/local/etc/php/php.ini
COPY ./apache/000-default.conf /etc/apache2/sites-available/000-default.conf

# composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# node
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs
