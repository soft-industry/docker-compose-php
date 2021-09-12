FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
	libicu-dev \
	default-mysql-client \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libonig-dev \
	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install iconv \
	&& docker-php-ext-install intl \
	&& docker-php-ext-install opcache \
	&& docker-php-ext-install mbstring \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

CMD ["php-fpm"]
