FROM php:7.4.4-fpm-alpine3.11

RUN apk add --update make curl nodejs

RUN docker-php-ext-install mysqli pdo pdo_mysql

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    ln -s $(composer config --global home) /root/composer
ENV PATH=$PATH:/root/composer/vendor/bin COMPOSER_ALLOW_SUPERUSER=1

ADD conf/php.ini /etc/php/conf.d/
ADD conf/php.ini /etc/php/cli/conf.d/
ADD conf/php-fpm.conf /etc/php/php-fpm.d/

WORKDIR /var/www/symfony

EXPOSE 9000

CMD ["php-fpm", "-F"]

