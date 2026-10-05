FROM php:8.5-fpm-alpine

RUN apk add \
    postgresql-dev \
    libzip-dev \
    freetype-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    gmp-dev \
    icu-dev \
    $PHPIZE_DEPS \
    imagemagick \
    imagemagick-dev \
    imagemagick-svg \
    librsvg \
    linux-headers

RUN pecl install apcu && docker-php-ext-enable apcu
RUN pecl install imagick && docker-php-ext-enable imagick

RUN docker-php-ext-configure gd --with-freetype --with-jpeg && docker-php-ext-install gd
RUN docker-php-ext-install exif && docker-php-ext-enable exif
RUN docker-php-ext-configure intl && docker-php-ext-install intl

RUN docker-php-ext-install \
    pdo_pgsql pgsql \	
    pdo_mysql mysqli \
    zip \
    gmp \
    sysvsem

WORKDIR /var/www/html

CMD ["php-fpm"]

