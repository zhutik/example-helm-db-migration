FROM php:fpm-alpine

ENV APP_PATH="/example-helm-db-migration"

WORKDIR $APP_PATH

COPY composer.json composer.lock $APP_PATH/
COPY . $APP_PATH

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
    composer install
