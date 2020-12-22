# Centos 7 basic image 
FROM centos:centos7.9.2009

# Maintainer name.
MAINTAINER Harish Jadhav

# Nextcloud required packages.
RUN yum -y install epel-release yum-utils wget unzip && yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm 
RUN yum-config-manager --disable remi-php54 && yum-config-manager --enable remi-php73
RUN yum -y install httpd php php-cli php-mysqlnd php-zip php-devel php-gd php-mcrypt php-mbstring php-curl php-xml php-pear php-bcmath php-json php-pdo php-pecl-apcu php-pecl-apcu-devel

# Download nextloud zipfile.
RUN cd /var/www/html/ && wget https://download.nextcloud.com/server/releases/nextcloud-20.0.4.zip
RUN cd /var/www/html/ && unzip nextcloud-20.0.4.zip
RUN cd /var/www/html/ && rm -rf nextcloud-20.0.4.zip

# Set container working directory.
WORKDIR /var/www/html/

# Create nextcloud data storage directory and update permissions.
RUN mkdir /var/www/html/nextcloud/data
RUN chown apache:apache -R /var/www/html/nextcloud

# Add apache virtualhost in to container.
ADD nextcloud.conf /etc/httpd/conf.d/

# Remove unwanted packages.
RUN yum -y remove epel-release yum-utils wget unzip http://rpms.remirepo.net/enterprise/remi-release-7.rpm 
RUN yum autoremove -y

# Start container.
CMD ["echo","Nextcloud new image successfully created and ready for use.!!!!!"]
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
EXPOSE 80
