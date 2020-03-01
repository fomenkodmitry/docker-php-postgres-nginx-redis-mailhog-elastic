FROM php:7.3-fpm-alpine


RUN apk add --no-cache \
    php7-pear \
    php7-dev \
    gcc \
    musl-dev make \
    libjpeg \
    libwebp \
    libpng \
    libpq \
    ghostscript \
    unzip \
    curl \
    imagemagick6 \
    freetype \
    libjpeg-turbo \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    imagemagick6-dev \
    libwebp-dev \
    libxml2 \
    libxml2-dev \
    libzip-dev \
    curl-dev \
    icu-dev \
    libpq \
    postgresql-dev \
    postgresql-contrib

RUN wget https://imagemagick.org/download/ImageMagick-6.9.10-86.tar.gz && \
    tar xvzf ImageMagick-6.9.10-86.tar.gz && \
    cd ImageMagick-6.9.10-86 && \
    ./configure && \
    make && \
    make install && \
    ldconfig /usr/local/lib

RUN pecl install xdebug \
    imagick

RUN docker-php-ext-configure gd \
        --with-gd \
        --with-freetype-dir\
        --with-png-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
        --with-webp-dir=/usr/include/ && \
    docker-php-ext-configure bcmath && \
    docker-php-ext-enable xdebug \
        imagick && \
    docker-php-ext-install \
        sockets \
        soap \
        zip \
        curl \
        bcmath \
        exif \
        gd \
        iconv \
        intl \
        mbstring \
        opcache \
        pdo_pgsql

