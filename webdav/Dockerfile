FROM ubuntu:18.04

RUN apt update
RUN apt install -y apache2
RUN mkdir -p /var/www/html/webdav
RUN chmod -R 777 /var/www/html/webdav
RUN chown -R www-data:www-data /var/www/html/webdav
RUN rm /etc/apache2/sites-available/*
RUN rm /etc/apache2/sites-enabled/*

COPY files/default.conf /etc/apache2/sites-available/webdav.conf
COPY files/passwd.dav /etc/apache2/passwd.dav

RUN a2enmod dav
RUN a2enmod dav_fs
RUN a2ensite webdav
RUN service apache2 stop
RUN sleep 1
RUN service apache2 start
RUN service apache2 start

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
