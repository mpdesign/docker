FROM php:7.1.11-fpm
MAINTAINER linqm <linqm@feiyu.com>

ENV PHPREDIS_VERSION 3.0.0


#RUN echo -e 'deb http://mirrors.aliyun.com/ubuntu/ quantal main restricted universe multiverse\n deb http://mirrors.aliyun.com/ubuntu/ quantal-security main restricted universe multiverse\n deb http://mirrors.aliyun.com/ubuntu/ quantal-updates main restricted universe multiverse\n deb http://mirrors.aliyun.com/ubuntu/ quantal-proposed main restricted universe multiverse\n deb http://mirrors.aliyun.com/ubuntu/ quantal-backports main restricted universe multiverse\n deb-src http://mirrors.aliyun.com/ubuntu/ quantal main restricted universe multiverse\n deb-src http://mirrors.aliyun.com/ubuntu/ quantal-security main restricted universe multiverse\n deb-src http://mirrors.aliyun.com/ubuntu/ quantal-updates main restricted universe multiverse\n deb-src http://mirrors.aliyun.com/ubuntu/ quantal-proposed main restricted universe multiverse\n deb-src http://mirrors.aliyun.com/ubuntu/ quantal-backports main restricted universe multiverse\n' > /etc/apt/sources.list


# source
RUN echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib\ndeb-src http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib" | tee /etc/apt/sources.list


#redis
RUN mkdir -p /usr/src/php/ext/redis \
    && curl -L https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
    && echo 'redis' >> /usr/src/php-available-exts \
    && docker-php-ext-install redis

RUN apt update && apt install -y wget unzip

RUN mkdir -p /usr/src/php/ext/yaf \
    && wget -P /usr/src/php/ext/yaf/ https://github.com/laruence/yaf/archive/master.zip  \
    && unzip /usr/src/php/ext/yaf/master.zip -d /usr/src/php/ext/yaf/ \
    && mv /usr/src/php/ext/yaf/yaf-master/* /usr/src/php/ext/yaf/ \
    && echo 'yaf' >> /usr/src/php-available-exts \
    #&& cd /usr/src/php/ext/yaf/ \
    && docker-php-ext-install yaf

RUN apt update && apt install -y libpng12-dev libjpeg-dev libzip-dev \
  && rm -rf /var/lib/apt/lists/* \
  && pecl install zip \
  && docker-php-ext-enable zip \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd mysqli pdo_mysql zip opcache redis bcmath yaf

