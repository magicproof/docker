FROM php:7.1-fpm-alpine

LABEL maintainer="magicproof@gmail.com"

# istall mysql and httpd.conf
RUN apk add --no-cache mysql-client  \
    apache2-proxy \
    && docker-php-ext-install pdo pdo_mysql

ENV APACHE_RUN_USER www-data \
    && APACHE_RUN_GROUP www-data \
    && APACHE_LOG_DIR /var/log/apache2

COPY ./modx /var/www/localhost/htdocs
COPY ./httpd.conf /etc/apache2/httpd.conf
WORKDIR /var/www
ENTRYPOINT ["/usr/sbin/httpd"]

CMD ["-DFOREGROUND"]
EXPOSE 80

