FROM php:7.1-fpm-alpine

LABEL maintainer="magicproof@gmail.com"

# istall mysql and httpd.conf
RUN docker-php-ext-install pdo pdo_mysql

# NGINX web server
RUN  apk add --no-cache nginx
COPY nginx.conf /etc/nginx/nginx.conf

RUN  apk add --no-cache mysql mysql-client
ENV  ROOT_PWD ackmodx
COPY my.cnf /etc/mysql/my.cnf
COPY mysql.sh /tmp/mysql.sh
RUN  sh /tmp/mysql.sh && rm /tmp/mysql.sh

COPY ./modx /home/modx
WORKDIR /home/modx

CMD [""]
EXPOSE 80
VOLUME ["/var/lib/mysql", "/home/modx"]

