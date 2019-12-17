
sudo yum update -y

sudo amazon-linux-extras install docker

sudo service docker start

sudo usermod -a -G docker ec2-user

sudo docker info

touch Dockerfile

docker build -t hello-world .

docker images --filter reference=hello-world

docker run -t -i -p 80:80 hello-world








FROM ubuntu:16.04

RUN apt-get update
RUN apt-get -y install apache2

RUN echo 'Hello Welcome!!' > /var/www/html/index.html

RUN echo '. /etc/apache2/envvars' >/root/run_apache.sh
RUN echo 'mkdir -p /var/run/apache2' >> /root/run_apache.sh
Run echo 'mkdir -p /var/lock/apache2'  >> /root/run_apache.sh
RUN echo '/usr/sbin/apache2 -D FOREGROUND'  >> /root/run_apache.sh
RUN chmod 755 /root/run_apache.sh
EXPOSE 80
CMD /root/run_apache.sh



sudo docker pull tomcat:8.0

sudo docker container create --publish 8082:8080 --name my-tomcat-container
tomcat:8.0

sudo docker container ls -a

sudo docker container start my-tomcat-container

sudo docker container exec -it my-tomcat-container bash

mkdir webapp

cd webapp

/home/ec2-user/webapp

Dockerfile:

# we are extending everything from tomcat:8.0 image ...
FROM tomcat:8.0
# COPY path-to-your-application-war path-to-webapps-in-docker-tomcat
COPY dac_demo.war /usr/local/tomcat/webapps/

wget https://dac-2019.s3.amazonaws.com/dac_demo.war

chmod 777 dac_demo.war

sudo docker image build -t tomcatwebapp .

sudo docker images

sudo docker container run -it --publish 8082:8080 tomcatwebapp1

chrome run
