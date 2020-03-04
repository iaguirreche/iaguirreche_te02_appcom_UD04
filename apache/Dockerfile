FROM ubuntu:18.04

RUN apt-get update && apt-get install -y apache2 \
    && apt-get -y install libapache2-mod-fcgid \
    && a2enmod proxy_fcgi \
    && apt-get install unzip

COPY 000-default.conf /etc/apache2/sites-available
COPY index.php /var/www/html
COPY wordpress-5.3.2-es_ES.zip /var/www/html

RUN unzip /var/www/html/wordpress-5.3.2-es_ES.zip -d /var/www/html

COPY wp-config.php /var/www/html/wordpress

EXPOSE 80
CMD ["apachectl", "-D", "FOREGROUND"]