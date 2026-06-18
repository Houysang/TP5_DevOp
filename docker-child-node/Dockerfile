FROM ubuntu:22.04

RUN apt update && apt install -y \
    apache2 \
    php \
    php-cli \
    php-mysql \
    php-curl \
    php-mbstring \
    php-xml \
    php-zip \
    php-bcmath \
    unzip \
    git \
    curl \
    composer

RUN a2enmod rewrite

WORKDIR /var/www/html

CMD service apache2 start && tail -f /dev/null