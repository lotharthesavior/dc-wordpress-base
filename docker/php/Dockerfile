FROM php:7.2.5-fpm

RUN apt-get update

COPY ./php-ini/php-custom.ini $PHP_INI_DIR/conf.d/
COPY ./php-ini/php-custom.conf /usr/local/etc/php-fpm.d/

# Install PDO and PGSQL Drivers
RUN apt-get install -y libpq-dev libpng-dev libjpeg-dev

# Install php extensions
# RUN docker-php-ext-install pdo pdo_mysql mysqli \
#     && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
#     && docker-php-ext-install json \
#     && docker-php-ext-install gd \
#     && docker-php-ext-install zip

RUN apt-get update && apt-get install -y \
    build-essential \
    default-mysql-client \
    openssl \
    zip \
    unzip \
    zlib1g-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libxml2-dev \
    libzip-dev \
    git \
    && docker-php-ext-install mbstring pdo_mysql mysqli zip json xml bcmath pcntl ctype \
    && docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

RUN docker-php-ext-configure gd \
    --with-gd \
    --with-jpeg-dir \
    --with-png-dir \
    --with-zlib-dir

# Install debug dependencies
RUN apt-get install git -y \
    && apt-get install vim -y \
    && apt-get install curl -y \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

