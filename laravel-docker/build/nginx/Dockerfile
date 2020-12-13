FROM ubuntu:20.04

RUN apt-get update && apt-get install -y nginx nano xvfb wget fontconfig libxrender1 xfonts-75dpi

COPY nginx.conf /etc/nginx/nginx.conf

ADD sites-enabled /etc/nginx/sites-enabled

ADD ssl /etc/nginx/ssl

RUN rm /etc/nginx/sites-enabled/default

WORKDIR /var/www/laravel-docker-app

EXPOSE 443

CMD ["nginx"]
