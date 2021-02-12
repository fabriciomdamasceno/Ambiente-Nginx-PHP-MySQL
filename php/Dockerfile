# FROM php:7.4-fpm-alpine
FROM php:8-fpm-alpine
RUN apk add --no-cache openssl bash nodejs npm
RUN docker-php-ext-install pdo pdo_mysql bcmath 

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html

EXPOSE 9000
ENTRYPOINT ["php-fpm"]
