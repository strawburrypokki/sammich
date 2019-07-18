FROM php:7.3-buster

WORKDIR /var/www/html

# Install utilitary tools
RUN apt-get -qq update && \
    apt-get -qq -y --no-install-recommends install git vim > /dev/null

# Install composer
RUN curl -s -o composer-setup.php https://getcomposer.org/installer && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer --quiet && \
    rm composer-setup.php

VOLUME /var/www/html

EXPOSE 80

USER www-data
