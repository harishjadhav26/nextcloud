# Ubunutu 21.04 basic image
FROM ubuntu:21.04

# Maintainer name.
MAINTAINER Harish Jadhav

# Set timezone in conatainer.
ENV TZ=Asia/Kolkata
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Nextcloud required packages installation.
RUN apt-get update
RUN apt-get install -y tzdata
RUN apt-get install -y debconf apt-utils
RUN export runlevel=1
RUN apt-get update && apt-get install -y apache2 wget unzip php zip libapache2-mod-php php-gd php-json php-mysql php-curl php-mbstring php-intl php-imagick php-xml php-zip php-mysql php-bcmath php-gmp
RUN export runlevel=1

# Download nextloud zipfile.
RUN cd /var/www/html/ && wget https://download.nextcloud.com/server/releases/nextcloud-20.0.4.zip
RUN cd /var/www/html/ && unzip nextcloud-20.0.4.zip
RUN cd /var/www/html/ && rm -rf nextcloud-20.0.4.zip

# Set container working directory.
RUN export runlevel=1
WORKDIR /var/www/html

# Create nextcloud data storage directory and update permissions.
RUN rm -rf /var/www/html/nextcloud-20.0.4.zip
RUN ls /var/www/html/ 
RUN mkdir /var/www/html/nextcloud/data
RUN chown -R www-data:www-data /var/www/html/nextcloud
RUN export runlevel=1

# Add apache virtualhost in to container.
ADD nextcloud.conf /etc/apache2/sites-available/
RUN export runlevel=1
RUN a2ensite nextcloud.conf
RUN a2enmod rewrite headers env dir mime setenvif ssl
RUN apache2ctl -t

# Remove unwanted packages.
RUN apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Set apache user and group.
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

# Start container.
CMD ["echo","Nextcloud new image successfully created and ready for use.!!!!!"]
CMD apachectl -D FOREGROUND
EXPOSE 80
