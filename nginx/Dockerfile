FROM ajoergensen/nginx-php-fpm:8.2

RUN apt install sudo 

RUN sudo curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

RUN apt update 

RUN sudo apt install nano

RUN sudo apt install -y mysql-client

RUN sudo apt install -y net-tools 

RUN sudo apt install -y init 

RUN sudo apt install -y systemd 

RUN sudo apt list php 

RUN apt-get update && apt-get install -y software-properties-common

RUN sudo apt-get update 

RUN sudo apt list php 

RUN sudo apt install -y php-fpm 

RUN sudo apt install -y php-common php-mysql php-cgi php-mbstring php-curl php-gd php-xml 

RUN sudo apt install -y nodejs

RUN sudo apt install -y npm

RUN sudo apt-get install -y git

WORKDIR /var/www/kbfira_docs/html/server

RUN npm install socket.io@4

RUN npm install uWebSockets.js@uNetworking/uWebSockets.js#v20.4.0

RUN npm install ini@3

RUN npm install zlib