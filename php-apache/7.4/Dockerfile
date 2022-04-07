FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
        libmcrypt-dev \
        libjpeg-dev \
        libpng-dev \
	vim \
	libzip-dev \
	zip \
	libc-client-dev \
	libkrb5-dev \
	libicu-dev \
    && pecl install mcrypt-1.0.4 \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-configure gd \
        --with-freetype=/usr/include/freetype2 \
        --with-jpeg=/usr/include \
    && docker-php-ext-install gd \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install gettext \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install imap \
    && docker-php-ext-install zip \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && a2enmod rewrite \
    && useradd joao \
    && sed -i 's|www-data|joao|g' /etc/apache2/envvars
