FROM alpine:3.1

LABEL maintainer="magicproof@gmail.com"

# NGINX web server with conf
RUN  apk add --update nginx
COPY nginx.conf /etc/nginx/nginx.conf

# istall php with ext
RUN apk add --update php-fpm php-pdo_mysql

#mysql
RUN  apk add --update mysql mysql-client
ENV  ROOT_PWD ackmodx
COPY mysql.sh /tmp/mysql.sh
RUN  sh /tmp/mysql.sh && rm /tmp/mysql.sh

# Supervisord
RUN  apk add --update supervisor
COPY supervisord.ini /etc/supervisor.d/supervisord.ini

#copy project
COPY ./modx /home/modx

WORKDIR /home/modx

CMD ["supervisord", "-c", "/etc/supervisord.conf", "-n"]
EXPOSE 80
#VOLUME ["/var/lib/mysql"]

