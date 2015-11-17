FROM birdsystem/docker-apache_base
MAINTAINER Allan Sun <allan.sun@bricre.com>

RUN apt-get update && \
    apt-get -yq install \
       php5-dev

# Install PHPUnit
# No xDebug to improve performance
RUN apt-get install -y ant && \
	composer global require "phpunit/phpunit=5.0.*" && \
    pecl channel-update pecl.php.net && \
	pecl install xdebug


# php.ini settings
ADD php_extra.ini /etc/php5/php_extra.ini

RUN ln -s /etc/php5/php_extra.ini /etc/php5/apache2/conf.d/99-php_extra.ini && \
	ln -s /etc/php5/php_extra.ini /etc/php5/cli/conf.d/99-php_extra.ini


# Clean apt-get cache to shrink image size
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /var/www/html