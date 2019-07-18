FROM debian:buster

# Install php7.3 (following this guide : https://computingforgeeks.com/how-to-install-php-7-3-on-debian-9-debian-8/)
## Add  PHP 7.3 PPA repository
RUN apt-get -qq update && \
    apt-get -y install git vim wget lsb-release apt-transport-https ca-certificates > /dev/null && \
    wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg && \
    echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee /etc/apt/sources.list.d/php7.3.list

## Install PHP 7.3 and its extensions
RUN apt-get -qq update && \
    apt-get -qq -y --no-install-recommends install \
    php7.3 \
    php7.3-cli \
    php7.3-fpm \
    php7.3-json \
    php7.3-pdo \
    php7.3-mysql \
    php7.3-zip \
    php7.3-gd \
    php7.3-mbstring \
    php7.3-curl \
    php7.3-xml \
    php7.3-bcmath \
    > /dev/null

RUN wget -qO composer-setup.php https://getcomposer.org/installer && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer --quiet && \
    rm composer-setup.php

ARG GIT_NAME
ARG GIT_EMAIL

RUN git config --system user.name $GIT_NAME && \
    git config --system user.email $GIT_EMAIL && \
    git config --system core.editor vim && \
    git config --system core.autocrlf false && \
    git config --system color.ui always

WORKDIR /var/www/html
RUN mkdir /var/www/.ssh && chown -R www-data:www-data /var/www/.ssh
VOLUME /var/www/html
EXPOSE 80
USER www-data
