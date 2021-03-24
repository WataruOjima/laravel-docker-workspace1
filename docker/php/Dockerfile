FROM php:7.4.1-fpm
# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN apt-get update \
&& apt-get install -y \
git \
zip \
unzip \
vim

RUN apt-get update && \
  apt-get -y install git unzip libzip-dev libicu-dev libonig-dev \
  zlib1g-dev \ 
  libjpeg-dev \
  libpng-dev \
  libfreetype6-dev \
  libjpeg62-turbo-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*
RUN docker-php-ext-install pdo_mysql zip bcmath
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install -j$(nproc) gd 
WORKDIR /var/www/html