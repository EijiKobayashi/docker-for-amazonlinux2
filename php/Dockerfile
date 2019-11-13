FROM php:7.2-fpm

# setup php
RUN apt-get update && apt-get install -y \
  gcc \
  make \
  vim \
  zip \
  unzip \
  iputils-ping \
  git \
  curl \
  libxml2-dev  \
  libsodium-dev \
  openssl \
  libpng-dev \
  curl \
  gnupg \
  libjpeg-dev \
  libfreetype6-dev \
  libmagickwand-dev \
  zlib1g-dev \
  libfreetype6-dev

# install php extension
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install dom
RUN docker-php-ext-install exif
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install hash
RUN docker-php-ext-install json
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install mysqli \
  && docker-php-ext-enable mysqli
RUN docker-php-ext-install sodium
RUN docker-php-ext-install xml
RUN docker-php-ext-install zip
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install iconv
RUN docker-php-ext-install simplexml
RUN pecl install imagick
RUN docker-php-ext-enable imagick

# put config
COPY ./php.ini /usr/local/etc/php/
