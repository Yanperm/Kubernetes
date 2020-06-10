FROM php:7.1-fpm-alpine
RUN apk update && apk add \
    build-base \
    libpng-dev \
    curl-dev \
    freetype \
    libpng \
    libjpeg-turbo \
    freetype-dev \
    libpng-dev \
    jpeg-dev \
    libjpeg \
    libjpeg-turbo-dev \
    git
  
RUN docker-php-ext-configure gd \
    --with-freetype-dir=/usr/lib/ \
    --with-png-dir=/usr/lib/ \
    --with-jpeg-dir=/usr/lib/ \
    --with-gd \
  && docker-php-ext-install \
    curl \
    gd \
    zip \
    pdo_mysql
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php --install-dir=/bin --filename=composer
RUN echo 'memory_limit = 1024M' >> /usr/local/etc/php/conf.d/docker-php-memlimit.ini;
WORKDIR /var/www/html
EXPOSE 9000
