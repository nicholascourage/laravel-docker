FROM ubuntu:20.04
ENV DEBIAN_FRONTEND noninteractive
#ENV REDIS_URL redis://redis_db:6379
RUN apt-get update && apt-get install -y \
  php-curl \
  php-fpm \
  php-gd \
  php-xsl \
  php-mysqlnd \
  php-cli \
  php-intl \
  php-bz2 \
  php-zip \
  php-mbstring \
  php-apcu \
  php-redis \
  php-bcmath \
  php-xmlrpc \
  && usermod -u 1000 www-data

ADD www.conf /etc/php/7.4/fpm/pool.d/www.conf
ADD php-fpm.conf /etc/php/7.4/fpm/php-fpm.conf
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
RUN ln -snf /usr/share/zoneinfo/Europe/Lisbon /etc/localtime
COPY init.sh /init.sh
RUN chmod +x /init.sh
EXPOSE 9000
CMD ["/init.sh"]
