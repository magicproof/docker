FROM alpine:3.1

LABEL maintainer="magicproof@gmail.com"

# NGINX web server with conf
RUN  apk add --update nginx \
    && rm -rf /var/cache/apk/*
COPY nginx.conf /etc/nginx/nginx.conf

# Supervisord
RUN  apk add --update supervisor \
    && rm -rf /var/cache/apk/*
COPY supervisord.ini /etc/supervisor.d/supervisord.ini

# istall php with ext
RUN apk add --update php-fpm php-pdo_mysql php-gd \
    && rm -rf /var/cache/apk/*

#mysql
RUN  apk add --update mysql mysql-client \
    && rm -rf /var/cache/apk/*
ENV  ROOT_PWD ackmodx
COPY mysql.sh /tmp/mysql.sh
RUN  sh /tmp/mysql.sh && rm /tmp/mysql.sh

#copy project
COPY ./modx /home/modx
COPY modx.sh /tmp/modx.sh
RUN  sh /tmp/modx.sh && rm /tmp/modx.sh

CMD ["supervisord", "-c", "/etc/supervisord.conf", "-n"]
EXPOSE 80
VOLUME /home/modx

