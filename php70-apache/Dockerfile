FROM php:7.0.22-apache
MAINTAINER David Lemaitre

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    imagemagick \
    mysql-client \
    locales \
    libxml2-dev \
    libicu-dev \
    libmcrypt-dev \
    libpng-dev \
    libcurl4-gnutls-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Enable Apache mods
RUN a2enmod rewrite alias headers expires

# Enable SSL
RUN a2enmod ssl && a2ensite default-ssl

# Set default ServerName
#RUN echo "ServerName localhost" > /etc/apache2/conf.d/fqdn.conf

# Set timezone
RUN echo "Europe/Paris" > /etc/timezone && dpkg-reconfigure -f noninteractive tzdata

# Reconfigure locales
RUN dpkg-reconfigure locales && \
    locale-gen C.UTF-8 && \
    /usr/sbin/update-locale LANG=C.UTF-8

RUN echo 'fr_FR.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen

# Install PHP extensions
RUN docker-php-ext-install \
    mysqli \
    pdo \
    pdo_mysql \
    soap \
    intl \
    mcrypt \
    gd \
    mbstring \
    zip \
    curl \
    json

# Export ports
EXPOSE 443
