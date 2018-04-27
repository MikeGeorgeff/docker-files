FROM php:7.2-fpm-alpine

MAINTAINER Mike Georgeff <mike.georgeff@uscca.com>

RUN apk --update add curl \
					 bash \
					 libxml2-dev \
					 nginx \
					 supervisor && \
					 docker-php-ext-install opcache pdo_mysql soap sockets && \
					 rm /var/cache/apk/* && \
					 mkdir /app && chown www-data:www-data /app

COPY nginx.conf /etc/nginx/nginx.conf
COPY settings.ini /usr/local/etc/php/conf.d/settings.ini
COPY supervisord.conf /etc/supervisord.conf
COPY nginx-supervisor.conf /etc/supervisor/conf.d/php-nginx.conf

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]

EXPOSE 80 443