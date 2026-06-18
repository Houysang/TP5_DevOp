FROM php:8.2-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    unzip \
    zip \
    nodejs \
    npm \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    && docker-php-ext-install \
        pdo_mysql \
        mbstring \
        exif \
        pcntl \
        bcmath \
        gd \
        zip \
        fileinfo \
        opcache

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working directory
WORKDIR /var/www/html

# Copy project (optional if using bind mount)
# COPY . .

# Install PHP dependencies (IMPORTANT)
RUN composer install --no-interaction --prefer-dist || true

# Install Node dependencies (optional safe fallback)
RUN npm install || true && npm run build || true

# Fix permissions (VERY IMPORTANT for Laravel)
RUN chown -R www-data:www-data /var/www/html

EXPOSE 9000

CMD ["php-fpm"]