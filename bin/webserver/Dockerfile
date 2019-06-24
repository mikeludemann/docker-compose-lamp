FROM php:7.1.20-apache

LABEL Mike Ludemann "mike-ludemann@hotmail.de"
LABEL version="1.0"

# Setup for environment
ENV CREATE 2019-06-24
# ENV DEBIAN_FRONTEND noninteractive

# Updating all sources
RUN apt-get update -y --fix-missing

# Upgrade all sources
RUN apt-get upgrade -y

# Install useful tools
RUN apt-get -y install apt-utils nano wget dialog

# Install important libraries
RUN apt-get -y install --fix-missing apt-utils build-essential git curl libcurl3 libcurl3-dev zip

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install xdebug
RUN pecl install xdebug-2.5.0
RUN docker-php-ext-enable xdebug

# Installing supervisord
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

# Installing ssh (Packages)
RUN apt-get install -y openssh-server openssh-client passwd
RUN mkdir -p /var/run/sshd

# Installing PHP 7 Extensions & more
RUN apt-get -y install libmcrypt-dev
RUN docker-php-ext-install mcrypt

RUN apt-get -y install libsqlite3-dev libsqlite3-0 mysql-client

RUN apt-get install -y libapache2-mod-php7.2 
RUN apt-get install -y php7.2
RUN apt-get install -y php7.2-mysql
RUN apt-get install -y php-xml
RUN apt-get install -y php7.0-mcrypt
RUN apt-get install -y php-cgi
RUN apt-get install -y php-cli
RUN apt-get install -y php-curl
RUN apt-get install -y php-gd
RUN apt-get install -y php-imagick
RUN apt-get install -y php-imap
RUN apt-get install -y php-pear

RUN docker-php-ext-install pdo_mysql 
RUN docker-php-ext-install pdo_sqlite
RUN docker-php-ext-install mysqli

RUN docker-php-ext-install git
RUN docker-php-ext-install svn

RUN docker-php-ext-install pwgen
RUN docker-php-ext-install curl
RUN docker-php-ext-install tokenizer
RUN docker-php-ext-install json

RUN apt-get -y install zlib1g-dev
RUN docker-php-ext-install zip
RUN docker-php-ext-install unzip

RUN apt-get -y install libicu-dev
RUN docker-php-ext-install -j$(nproc) intl

RUN docker-php-ext-install mbstring

RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ 
RUN docker-php-ext-install -j$(nproc) gd

# Enable apache modules
RUN a2enmod rewrite headers
