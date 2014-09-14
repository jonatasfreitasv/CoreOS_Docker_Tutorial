#Dockerfile

#Imagem que vai ser utilizada como base
FROM ubuntu:12.04

#Instala pacotes
RUN apt-get update -y
RUN apt-get install -y apache2 -y
RUN apt-get install php5 libapache2-mod-php5 php5-mcrypt -y
RUN apt-get install git -y

#Clona repositório do Linux Dash dentro da pasta Dash
WORKDIR /var/www
RUN git clone https://github.com/afaqurk/linux-dash.git dash

#Define váriaveis do so
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

#Expoe a porta 80 do container
EXPOSE 80

#Inicializa o apache
ENTRYPOINT ["/usr/sbin/apache2"]

#Define comandos de inicialização do docker run
CMD ["-D", "FOREGROUND"]