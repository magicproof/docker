FROM php:7.2.6-fpm

RUN apt-get update && apt-get -qq -y install curl libpng-dev
    
RUN docker-php-ext-install gd mbstring

COPY . /var/www/myapp
WORKDIR /var/www/myapp

CMD [ "php", "./index.php" ]

