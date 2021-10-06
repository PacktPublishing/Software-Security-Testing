FROM ubuntu

MAINTAINER info@cyberacademy.co

ENV DEBIAN_FRONTEND='noninteractive' 
RUN apt-get -y update
RUN apt-get -y install apt-transport-https lsb-release dnsutils ca-certificates mariadb-server wget unzip supervisor \
	&& DEBIAN_FRONTEND='noninteractive' apt-get autoremove -y \
	&& DEBIAN_FRONTEND='noninteractive' apt-get clean

#RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
#RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
RUN apt install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get -y install php5.6
RUN apt install -y php5.6-cli php5.6-common php5.6-curl php5.6-mbstring php5.6-mysqlnd php5.6-xml

RUN /etc/init.d/mysql start\
	&& mysql -e "grant all privileges on *.* to 'root'@'localhost' identified by 'bug';" \
	&& mysql -u root -pbug -e "show databases;" \
	&& DEBIAN_FRONTEND='noninteractive' apt-get autoremove -y \
	&& DEBIAN_FRONTEND='noninteractive' apt-get clean

WORKDIR /var/www/html/

COPY ./supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY ./web_vulns.zip .

RUN unzip web_vulns.zip \
	&& sed -i 's/db_password = ""/db_password= "bug"/' ./web_vulns/admin/settings.php \
	&& sed -i 's/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www\/html\/web_vulns/' /etc/apache2/sites-available/000-default.conf \
	&& sed -i 's/allow_url_include = Off/allow_url_include = On/g' /etc/php/5.6/apache2/php.ini \
	&& rm /var/www/html/index.html \
	&& chown www-data:www-data /var/log/apache2 \
	&& chown www-data:www-data /var/log/apache2/access.log \
	&& chown www-data:www-data /var/log/apache2/error.log

RUN /etc/init.d/mysql restart && /etc/init.d/apache2 restart &&\
	wget http://127.0.0.1/install.php?install=yes 1>/dev/null

EXPOSE 80

CMD ["/usr/bin/supervisord"]
