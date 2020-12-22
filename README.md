# Nextcloud Dockerfile

#### For Centos use centos dorectory to create nextcloud image.

cd PATH/centos7

time docker build -t nextcloud:20.0.4-cent7.9 .

#### For Ubuntu use ubuntu dorectory to create nextcloud image.

cd PATH/ubuntu

time docker build -t nextcloud:20.0.4-ubuntu21.04 .

#### This process takes some time once done check image

docker images

#### Start container execute following command.

docker run -itd -p 8080:80 IMAGENAME

#### On browser access nextcloud.

http://IP/HOSTNAME:8080 <---------------- For centos

#### AND for ubuntu container.

http://IP/HOSTNAME:8080/nextcloud <---------------- For ubuntu

#### Also, if you do not want to build then pull updated images from dockerhub using following command.

docker pull harishjadhav26/nextcloud:20.0.4-cent7.9

#### Start container execute following command.

docker run -itd -p 8080:80 harishjadhav26/nextcloud:20.0.4-cent7.9


