FROM php:8.3.9-fpm-alpine3.20 AS base

ARG user
ARG group

COPY docker/php/www.conf /usr/local/etc/php-fpm.d/
COPY --from=composer/composer:2.7.7-bin /composer /usr/bin/composer
COPY --chown=$user:$group . /var/www/wapi

RUN cd /var/www/wapi && composer install

EXPOSE 9000
USER $user
CMD ["php-fpm"]
