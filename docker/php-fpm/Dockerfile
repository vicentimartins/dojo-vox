FROM php:8-fpm

# App dir
RUN useradd vox
RUN mkdir /app;
RUN chown -R vox:vox /app
RUN chmod -R 777 /app
WORKDIR /app

# Basic install
RUN apt update; \
    apt autoremove -y; \
    apt install -y \
    libpq-dev \
    zip \
    unzip \
    git;

RUN docker-php-ext-install pdo \
    pdo_pgsql;

RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Enable xdebug
RUN pecl install xdebug; \
    docker-php-ext-enable xdebug;

# Install composer
COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

USER vox
