FROM php:8.3-fpm

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libpq-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    postgresql-client \
    zip \
    curl \
    nodejs \
    npm \
    && docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
    && docker-php-ext-install pdo pdo_pgsql mbstring exif pcntl bcmath gd zip


    
COPY --from=composer:2.7 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

RUN npm install -g fantasticon

RUN mkdir -p /var/www/.npm && chown -R www-data:www-data /var/www/.npm

COPY ./docker/development/php-fpm/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh

COPY --chown=www-data:www-data . .

USER www-data
RUN composer install --optimize-autoloader
RUN npm ci && npm run build

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

EXPOSE 9000

# Запускаем php-fpm в режиме "демон off"
CMD ["php-fpm"]