Docker All Practise: Khaja Sir’s Class:
>> Docker Installation:
curl -fsSL https://get.docker.com -o install-docker.sh
sh install-docker.sh
docker info
sudo docker info
Cat /etc/group
Whoami
Docker info 
sudo usermod -aG docker ctrls
# exit
# relogin
Docker info 

Docker container run hello-world
Again>
Docker container run hello-world
Docker container run -d alpine
Again>
Docker container run -d alpine
docker image ls
--Generations
Docker images
Docker image ls
Docker ps -a
Docker container ls -a
--
Docker –help
Docker image –- help
Docker image ls –- help
Docker container – help

Docker container rm –- help
Docker cheat sheer >> helpful for find out the commands
Docker network – help
Docker network create – help
Docker volume –- help
Figure out docker commands
•	create a docker network > docker network create
•	list docker volumes > docker volume ls
•	stop the docker container > docker stop my_container
•	remove the docker image > docker image rm
•	build the docker image > docker image build
•	start all the containers using docker compose > docker compose up -d
•	stop all the containers docker compose > docker compose stop
ps
04/01/2023:
Java -version
Docker container run -it openjdk:11 /bin/bash
Java -version >> inside container
Cat /etc/passwd
Docker container run -it alpine /bin/sh
Cat /etc/passwd >> inside container
ps aux - it is on docker host
docker container run -it alpine /bin/sh
ps aux
df -h
exit
df -h
ip addr
docker container run -it alpine /bin/sh
ip addr >> inside Container
docker container run -d –name test1 httpd
docker container run -d –name test2 –-m httpd
docker container run -d –name test2 –memory 128M httpd
docker status
docker container run -it openjdk:11 /bin/bash
whereis java >> inside
docker container run -it openjdk:8 /bin/bash
whereis java
exit
docker container run –help
Port forwarding:
docker container run -p 32000:80 -d nginx
docker container ls
one more for same port, it will fails
docker container run -p 32000:80 -d nginx
docker container rm -f $(docker container ls -a -q)
docker container run -d -P nginx
docker container ls
docker container run -d -P nginx
docker container ls

docker container run -d -P nginx  >> Name or Port automictically. 
docker container ls
docker container run –help
docker container -d -P –- name webapp1 nginx
docker container ls
Date: 05-01-2023
docker container run --name apache -d -P httpd
docker container ls
docker container stop apache
docker container rm apache (we can do only container is in stopped state)
docker container rm -f apache (forceful deletion)

docker container run --name nginx -d -P nginx
docker container ls
docker container stop nginx
docker container rm nginx

docker container rm -f nginx
--
Docker container run –- name mysql -d -P mysql
Docker container ls

Run this is an above process
•	mysql
•	postgres
•	mongodb

DATE: 06-01-2023
sudo apt update && sudo apt install apache2 -y

sudo apt install apache2
sudo systemctl status apache2
curl http://localhost
cd /var/www/html/
ls
sudo mv index.html index
sudo vi 

--
Docker container run -d -P – name mycontainer -it httpd /bin/bash

Docker container exec -it <name/id> /bin/bash
# creates the container and runs in the background
docker container run -d -P --name mycontainer httpd

docker container exec -it mycontainer /bin/bash
ls
cd htdocs/
ls > index.html
cat index.html
echo "<h1> This is my home page </h1>" > /usr/local/apache2/htdocs/index.html
docker container –help
docker container commit –help
docker container commit mycontainer myfirstimage
docker image ls
docker container run –name first container -d -P myfirstimage
docker container ls
docker container exec firstcontainer pwd
--------------\
Dockerfile :
Mkdir myfirstimage
Cd myfirstimage
Vi dockerfile
FROM httpd
EXPOSE 80
RUN echo "<h1> This is my home page </h1>" >  /usr/local/apache2/htdocs/index.html

Docker image build -t myfirst:1.0 .
Docker image ls
Docker container run -d -P – name first myfirst:1.0
Manual Steps:
1VM with ports all enabled
sudo apt update && sudo apt install apache2 -y

ctrls@manualtest:/var/www$ cd html
ctrls@manualtest:/var/www/html$ ls
index.html
ctrls@manualtest:/var/www/html$ sudo mv index.html index-orig.html
ctrls@manualtest:/var/www/html$ sudo vi index.html
<h1> Bokkalo image ni edit chesanu but congraguation to edit </h1>
Browse the page:
--
Manual approach using containers
docker container run -d -P --name mycontainer httpd
docker container exec -it mycontainer /bin/bash
ls 
cd htdocs
echo "<h1> This is my home page </h1>" > index.html
browse the page and check the validation:
•	Now create a image from container
docker container commit mycontainer firstimage

docker container run –name firstcontainer -d -P myfirstimage
docker container exec -it firstcontainer /bin/bash
# cd htdocs
Cat index.html

echo "<h1> Khaja Sir Class understood as of now</h1>" > index.html
Browser Refresh adnd edited:
Docker container stop mycontainer myfirstcontainer
Docker container rm mycontainer myfirstcontainer
Or 
docker container rm -f $(docker container ls -a -q)
To delete images:
docker image ls
docker image ls -q
docker image rm $(docker image ls -q)
Docker File:
Cd myfirstimage
Vi dockerfile
--
FROM httpd
EXPOSE 80
RUN echo "<h1> This is my home page </h1>" >  /usr/local/apache2/htdocs/index.html
--
Docker image build -t myfirst:1.0 .
Docker image ls
Docker container run -d -P –name firstcontainer myfirst
Browse the Page and see the result
Cat dockerfile
Mkdir test
Vi dockerfile
--
From httpd

Docker image build -t test:1.0 .
Docker image ls
Docker image pull httpd (# it is not downloding)
Docker image ls

--
From scratch

Docker image build -t test:1.1 .
Docker image ls

Docker container run -d -P test:1.0
Docker container rm -f $(docker container ls -a -q)

Docker container 

From httpd:2.4.58

FROM httpd:2.4.58
RUN  echo "hello"

Docker image build -t test3.0 .
Docker image ls
FROM httpd:2.4.58
RUN  touch 1.txt

docker image build -t test3.1 .
docker image ls

Spring Petclinec: 1.35.00.

$ docker container run -it amazoncorretto:17-alpine3.17-jdk /bin/sh
wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-3.1.0-SNAPSHOT.jar
wget – version
curl – version
java -jar spring
docker container run -d alpine sleep 10
docker container ls

docker image build -t spc:1.0 .
docker image ls
docker container run -d -P –- name myspc spc:1.0
docker container ls
FROM httpd:2.4.58
RUN  echo "hello"

FROM httpd:2.4.58
RUN  touch 1.txt

Game of life War:

docker image build -t gol:1.0 .
docker image ls
docker container run -d -P – name gol gol:1.0
docker container ls

resfresh the browser
/gameoflife
Cp Dockerfile mydockerfile 
>> Replce with Copy ./gameoflif
Docker image build –- help
Docker image build -f mydockerfile -t gol:other .
docker container run -d -P – name golother gol:other


Workdir Concepts:
docker container rm -f $(docker container ls -a -q)

Docker container run -d -P – name sample1 nginx
Docker container run -d -P – name sample2 tomcat:9-jdk8
Docker container run -d -P – name sample3 jenkins/jenkins
Docker container ls
Docker container rm -rf gol
Docker container exec sample1 pwd
>/
Docker container exec sample2 pwd
>/user/local/tomcat
Docker container exec sample3 pwd
>/

Modify the Dockerfiles
Springpetclinic>>
FROM amazoncorretto:17-alpine3.17-jdk
LABEL author="khaja" 
LABEL project="learning"
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-3.1.0-SNAPSHOT.jar /spc/spring-petclinic-3.1.0-SNAPSHOT.jar
WORKDIR /spc
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]

#FROM amazoncorretto:17-alpine3.17-jdk
#LABEL author="khaja" 
#LABEL project="learning"
#RUN wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-3.1.0-SNAPSHOT.jar
#EXPOSE 8080
#CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]

docker image build -t spc:1.0 .
docker image ls
docker container run -d -P – name spcnew spc:1.0

docker container exec sample1 whoami
docker container exec sample2 whoami
docker container exec sample3 whoami
docker container exec sample4 whoami
## USER Concept:
>>>>>
Edit the spring petclinc Dockerfile

Docker image build -t spc:nonroot .
Docker container rm -f sample4
Docker container run -d – name sample4 -P spc:nonroot
Docker container ls
Docker container logs sample4
Docker stats
Docker container exec sample4 pwd 
Docker container exec sample4 whoami
 ## Paramiterization:
## args:
>>>>>
Edit the spring petclinc Dockerfile

Docker image build -t spc:1.0 .
Docker image ls
Docker container run -d -P – name Spcexp1 spc:1.0
Docker container ls
Docker container exec spcexp1 pwd

>>>




IMAGE Layers:

Docker image pull python:slim
Docker image pull openjdk:8
Docker image pull openjdk:11
Docker image pull alpine
Mkdir exp
Cd exp/
Vi dockerfile
>
FROM alpine
RUN touch 1.txt
Docker image build -t exp:1.0 .
Vi dockerfile
>
FROM alpine
RUN touch 1.txt
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/gameoflife.war /gameoflife.war

Docker image build -t exp:2.0 .
Docker image ls
Docker image inspect alpine : sha256:d4fc045c9e
>> write Down the layer 
Docker image inspect exp:1.0
>> write down the layer :: 
sha256:d4fc045c9e
sha256:191f293290
Dcker image inspect exp:2.0
>> write down the layer
sha256:d4fc045c9e3a848011de66f34b81f052d4f2c15a17bb196d637e526349601820",              sha256:191f29329068e47e46ac08709515e8ae8ddb7e246eaf5b2d7140d3afce3ee40f",                sha256:d318847c9d68fcbd5f80f6800caea12b97a6cdc3a500c7b64f2f8283899c9f0e"
Docker image pull openjdk:17
Docker image pill openjdk:11
Docker image pull openjdk:8
>>
Docker container run -it exp:2.0 /bin/sh
Touch 2.txt
Rm 1.txt
Rm gameoflife.war
--------------
FROM alpine
RUN apk add java
RUN touch 1.txt
Or
RUN apk add java && touch 1.txt



docker image ls
docker image inspect openjdk:8
>>>>>>>>
Docker Container lifecycle:
Docker container rm -f $(docker container ls -a -q)
Docker image rm -f $(docker image ls -q)
Docker container run –name nginx -d -P nginx
Docker container sls
Docker container stop nginx
Docker container ls -a
Docker container start nginx
Docker container ls -a
Docker container pause nginx
Docker container ls -a > No Hardware details shared
Docker container unpause nginx
Docker container ls -a
Docker container rm ngix
--
Docker Volume Concept:
Docker volume ls
Docker volume – help
Docker volume create – help
Docker volume ls
Docker volume create mysql-vol
Docker volume ls
Docker volume inspect mysql-vol
Docker image pull mysql:8.0
docker container run -d -P –-name mysqlwithoutvol -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops mysql:8.0
Docker container ls
docker container run -d –-name mysqlwithvol -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops -v mysql-vol:/var/lib/mysql mysql:8.0

Lets take Docker playground
Docker container ls
Docker container exec -it mysqlwithoutvol mysql -u devops -p
Show databeses
Use emp;
mysql create and insert into table > search in browser
CREATE TABLE authors (id INT, name VARCHAR(20), email VARCHAR(20));
SHOW TABLES;
INSERT INTO authors (id,name,email) VALUES(1,"Vivek","xuz@abc.com");

INSERT INTO authors (id,name,email) VALUES(2,"Priya","p@gmail.com");
mysql> 
INSERT INTO authors (id,name,email) VALUES(3,"Tom","tom@yahoo.com");
SELECT * FROM authors;
Exit:
Same do with Mysqlwithvolume:
Docker container exec -it mysqlwithvol mysql -u devops -p
Show databeses
Use emp;
mysql create and insert into table > search in browser
CREATE TABLE authors (id INT, name VARCHAR(20), email VARCHAR(20));
SHOW TABLES;
INSERT INTO authors (id,name,email) VALUES(1,"Vivek","xuz@abc.com");

INSERT INTO authors (id,name,email) VALUES(2,"Priya","p@gmail.com");
mysql> 
INSERT INTO authors (id,name,email) VALUES(3,"Tom","tom@yahoo.com");
SELECT * FROM authors;

Exit 
--
docker container rm -f $(docker container ls -a -q)
Again  Create Container
docker container run -d -P --name mysqlwithoutvol -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops mysql:8.0
docker container run -d -P --name mysqlwithvol -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops -v mysql-vol:/var/lib/mysql mysql:8.0
docker container exec -it mysqlwithoutvol mysql -u devops -p
Use emp;
Show tables;
Exit
Bye


docker container exec -it mysqlwithvol mysql -u devops -p
Use emp;
SELECT * FROM authors;>> we get the data
Exit
Bye

## same with withour volume
Docker 
Use emp;
Show * from authors;

--
Docker volume ls
Docker Volume instruction:
Docker container run -d httpd
Docker volume ls
docker container run -d -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops mysql:8.0
docker container run -d -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops mysql:8.0
docker container run -d -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops mysql:8.0
docker container run -d -P -e MYSQL_ROOT_PASSWORD=rootroot -e MYSQL_DATABASE=emp -e MYSQL_USER=devops -e MYSQL_PASSWORD=devops -v mysql-vol:/var/lib/mysql mysql:8.0
docker volume inspect mysql-vol
Sudo ls -al -----------Mysql patch Above---
--
BIND Mount:
Mkdir test
Touch test/{1..100}.txt
docker container run -d --name test -v /root/test:/data alpine sleep 1d
docker container exec -it test /bin/sh
##Ls /data
touch /data/{100..200}.txt
Ls test/

rm -rf test/
docker volume create test-vol
docker volume – help
docker volume prune
docker volume ls
 
Dockerfile for nopcommerce::
Creat VM
>>
Docker Install

docker container run -it -p 5000:5000 manual mcr.microsoft.com/dotnet/runtime:7.0 /bin/bash
dotnet --list-runtimes
https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.6/nopCommerce_4.60.6_NoSource_linux_x64.zip
apt update
apt install unzip -y
mkdir nop
mv nopCommerce_4.60.6_NoSource_linux_x64.zip nop/
cd nop
unzip nopCommerce_4.60.6_NoSource_linux_x64.zip
sudo mkdir bin
sudo mkdir logs
dotnet Nop.Web.dll
browse with public ip :5000 port
expose asp.net docker in google
dotnet Nop.Web.dll –- urls “http:/0.0.0.0:5000”
browse with public ip :5000 port
exit


FROM mcr.microsoft.com/dotnet/runtime:7.0
EXPOSE 5000
ARG
DOWNLOAD_URL= https://github.com/nopSolutions/nopCommerce/releases/download/release-4.60.6/nopCommerce_4.60.6_NoSource_linux_x64.zip
ADD ${DOWNLOAD_URL} /nop/nopCommerce_4.60.6_NoSource_linux_x64.zip
RUN apt update && apt install unzip -y && cd /nop && unzip nopCommerce_4.60.6_NoSource_linux_x64.zip && 
mkdir bin logs
ENV ASPNETCORE_URLS=http://0.0.0.0:5000
Or
CMD [“dotnet”, “Nop.Web.dill”, “--urls”, “http://0.0.0.0:5000”]

Need to learn from Linux:
1.Package Managers (apt, yum)
2. daemons
3.linux startup, user logins (bashrc.)
4. Install and Configure mysql, postgres, mongodb, tomcat,nginx,ha Procy
5.what is D/F sudo apt upfrade/ apt update

PONGAL -Holidays:

Need to revision all the above 

Post PONGAL -Holidays:
Date:: 19-01-2024
Containerize Nop commerce: Dockerfile
	Take a server from docker Playground
Mkdir nopcommerce
Cd 
Vi dockerfile
>>

Docker image pull dontnet7.0
Wget 
Mkdir nop
Mv nopsommer nop
Cd nop/
Unzip 
Mkdir bin logs
Cd ..
Vi dockerfile
Docker image build -t nop:0.01 .
Docker container run -it -p 32000:5000 nop:0.0.1 /bin/bash 
Ls
Dotnet Nop.Web.dll –urls http://0.0.0.0:5000

Browser Working:

Docker container ls -a
Docker container rm -f <name of container>

Vi Dockerfile

Docker container run -d -P – name nop nop:1.0
Docker container ls
Docker container inspect nop
Cat Dockerfile:
>>>

>>
Docker container inspect nopdb
>>
admin@lt.com
admin@123

172.17.0.3
Nop
Nop
Nop12345
>>>
Docker container ls -a
Docker container stats
Docker volume inspect nopdbcd 
If you want see the all the files in nop mysql files >> routing back to data

Docker Netwotking:

ifconfig
sudo apt update && sudo apt install net-tools -y
ifconfig
Install Docker in Linux Server using Azure/Aws
docker container run -it –name test alpine /bin/sh
#ifconfig
Exit

Docker container rm test
docker container run -d – name d1 alpine sleep 1d
docker container run -d – name d1 alpine sleep 1d
docker container inspect d1
docker container inspect d2
docker container exec -it d1 /bin/sh
ping d2
	Bad addres
Ping 172.17.0.3
	Not by its name it is not working
>>
Docker network drivers:
Bridge between 2 networks using network bridge

Docker network –help
Docker network ls
Docker network inspect bridge
Docker network – help
Docker create – help
Docker network create -d bridge – subnet 192.168.100.0/24 mybridge
Docker network ls
Ifconfig > our new range come
Docker container run -d –name c1 – network mybridge Alpine sleep 1d
Docker container run -d –name c2 – network mybridge Alpine sleep 1d
Docker container inspect mybridge 
Docker container exec -it c1 /bin/sh
#> Ping c2
 Ping 192.168.100.3
## we can ping the server with both hostname and ping
>>>> >>>>> >>>> >>>>> >>>> >>>> >>>> 
Docker container ls
Docker network connect – help
Docker network connect mybridge d1
Docker container inspect d1
Docker container exe c-it c1 /bin/sh
Ping d1
>> it is pinging
Ping d2 
>> it is not working
Docker network – help >> disconnect

Sets Resources limit:
Docker Swarm:
3 servers from docker playground:
Docker network ls >> check in all 3 servers like manager , node 1, node 2
Docker swam init 
Join
Docker network ls
Docker network ls
Docker service – help
Docker service create – help
Docker service create – replicas 5 nginx
Docker container ls
Docker service ls
Docker service ps dreamy_fermat
Docker service – help
Docker service scale –help
Docker service scale dreamy_fermat=10
Docker service scale dreamy_fermat=1
Docker service ps dreamy_fermat
We can do multiple things from service based upon the basic discussion:
Docker container ls
Docker container exec -it  /bin/bash
# apt update
Ip addr
Apt install net-tools;
Ipconfig

## Activtes:
•	Refer Here for reference
•	Create an nginx container with 256 MB RAM
•	Create a tomcat container with 128 MB RAM and 1 CPU
•	Refer Here for YAML Tutorial.

Multistate Docker file:: 
1)	Azure VM with Docker installed:
     2)Git clone :
>> git clone https://github.com/spring-projects/spring-petclinic.git
>> ls
>> cd spring-petclinc
>> vi docker file

>> docker image build -t spc:0.1 .
>>docker container run -it – name spctrail spc:0.1 /bin/bash
>>ls
>>pwd
>>ls target/
>> again write Docker file
Docker container rm -f spctrial
Vi dockerfile
:wq!
docker image build -t spc:1.0 .
docker image ls
docker container run -d –-name spctrail -P spc:1.0
Docker container ls
Browse : 
Scanning is required to proceed the security venerability
--
sudo apt-get install wget apt-transport-https gnupg lsb-release
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
sudo apt-get install trivy

--
Docker image – help

Trivy image spc:1.0
docker container run -it –-name tbd  amazoncorretto:17-alpine-jdk /bin/sh
adduser – help
adduser -s /bin/sh spc  >> #
addgroup – help
addgroup lt    >> #
adduser -s /bin/sh -g lt -D lt  >>#
adduser -s /bin/sh -D lta
cat /etc/group
Cat /etc/passwd

Cd ..
mkdir javabase
cd javabase
vi dockerfile
--
From 
RUN adduser -D -s /bin/sh lt
USER lt
----
docker image build -t ltjava:17 .
Dokcer image ls
trivy image ltjava:17
Again Edit docker file

 cd..
mkdir javabse 
cd javabase
vi dockerfile
docker image build -t ltjava:17 .
From 01.00.00 Hrs
NOP Commerce:
Cd nopcommerce/
rm Dockerfile
vi dockerfile
 

---




 

























