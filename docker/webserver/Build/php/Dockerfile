FROM php:8.0.22-fpm-alpine
ENV localdir = /var/www/html/username
RUN apk update; \
    apk upgrade; \
    apk add nano;
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo pdo_mysql
COPY confs/php.ini /usr/local/etc/php/php.ini
RUN rm "/usr/local/etc/php/php.ini-production"
RUN rm "/usr/local/etc/php/php.ini-development"
RUN apk add curl php-curl
COPY --from=composer /usr/bin/composer /usr/bin/composer
RUN composer global require "laravel/installer=~1.1"
RUN echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc

RUN mkdir -p ${localdir}
