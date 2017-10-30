#FROM hub-mirror.c.163.com/php:7.0.9-fpm
MAINTAINER linqm <linqm@feiyu.com>

ENV PHPREDIS_VERSION 3.0.0


#redis
RUN mkdir -p /usr/src/php/ext/redis \
    && curl -L https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
    && echo 'redis' >> /usr/src/php-available-exts \
    && docker-php-ext-install redis

RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev \
  && rm -rf /var/lib/apt/lists/* \
  && pecl install zip \
  && docker-php-ext-enable zip \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd mysqli pdo_mysql zip opcache redis bcmath

# yaf
RUN mkdir -p /usr/local/yaf/ && \
    wget -P /usr/local/yaf/ https://github.com/laruence/yaf/archive/master.zip && \
    unzip /usr/local/yaf/master.zip -d /usr/local/yaf/ && \
    cd /usr/local/yaf/yaf-master/ && \
    phpize && ./configure && make && make install && \
    rm -rf /usr/local/yaf
#COPY ./config/yaf.ini /usr/local/etc/php/conf.d/
#COPY ./config/php.ini /usr/local/etc/php/conf.d/
