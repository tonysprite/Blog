FROM php:7.3-fpm

RUN apt-get update && apt-get install -y cmake libssl-dev wget librabbitmq-dev zlib1g zlib1g.dev git zip \
    && apt install -y libzip-dev \
    && docker-php-ext-install pdo pdo_mysql mysqli bcmath \
    && pecl install redis-4.0.1 amqp zip grpc protobuf psr phalcon\
    && docker-php-ext-enable redis amqp phalcon grpc protobuf zip psr phalcon \
    && cd /tmp && wget https://install.phpcomposer.com/installer \
    && mv installer ./composer-setup.php \
    && php composer-setup.php && mv composer.phar /usr/local/bin/composer \
    && cd /tmp && rm -rf ./* \
    && cp -ap /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

## 把当前目录 挂载到镜像路径
WORKDIR /var/www/html/blog