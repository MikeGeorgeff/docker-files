FROM php:7.2-alpine

MAINTAINER Mike Georgeff <mike.georgeff@uscca.com>

RUN apk --update add curl \
					 bash \
					 libxml2-dev \
					 supervisor && \
					 docker-php-ext-install pdo_mysql soap sockets && \
					 rm /var/cache/apk/* && \
					 mkdir /app

COPY supervisord.conf /etc/supervisord.conf
COPY php.ini /usr/local/etc/php/php.ini

ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]

WORKDIR /etc/supervisor/conf.d/