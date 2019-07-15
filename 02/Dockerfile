FROM php:7.1-fpm-alpine

LABEL maintainer="magicproof@gmail.com"

# istall mysql and httpd.conf
RUN apk add --no-cache mysql-client  \
    apache2 \
    && docker-php-ext-install pdo pdo_mysql

ENV APACHE_RUN_USER www-data \
    && APACHE_RUN_GROUP www-data \
    && APACHE_LOG_DIR /var/log/apache2

COPY . /var/www//usr/localhost/htdocs/
ADD httpd.conf /etc/apache2
WORKDIR /var/www/html
ENTRYPOINT ["/usr/sbin/httpd"]

CMD ["-DFOREGROUND"]
EXPOSE 80

