
* Docker installation & add the user to Docker group
--
 *  docker info
 *  curl -fsSL https://get.docker.com -o install-docker.sh
 *  sh install-docker.sh
 *  sudo usermod -aG docker qtdevops
 *  ls
 *  docker info
 *  docker --version
 * 
--
* Docker images creation & Container running
sudo apt update -y
sudo apt-get install -y net-tools

docker container run -p 32000:80 -d nginx
docker container run -P -d --name nginx nginx
docker image ls
docker container ls
docker --help
docker container ls -a -q
docker image ls -a -q
docker container rm -f $(docker container ls -a -q)
docker image rm -f $(docker image ls -a -q)
--
docker container run --name apache -d -P httpd
docker container ls
docker container stop apache
docker container rm apache
--
* Docker File Creation
FROM amazoncorretto:17-alpine3.17-jdk
LABEL author="Arifulla"
LABEL project="learning"
ADD https://spcjarfile.blob.core.windows.net/spcjar/spring-petclinic-3.2.0-SNAPSHOT.jar?sp=r&st=2024-03-27T10:19:06Z&se=2024-03-28T18:19:06Z&spr=https&sv=2022-11-02&sr=b&sig=ZXNXQMlCPf0aeMWLhsy%2FoCXR5L3muSsRxSvjW%2BQC56I%3D /spring-petclinic-3.1.0-SNAPSHOT.jar
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]
--
* Docker file with Root for above and we need to creat the Normal User for this
FROM amazoncorretto:17-alpine3.17-jdk
LABEL author="khaja" 
LABEL project="learning"
EXPOSE 8080
# creates a new group and user
RUN addgroup -g 1000 spc && adduser -h "/spc" -u 1000 -G spc -s /bin/bash -D spc
# switching to user spc
USER spc
# Download the file
ADD --chown=spc:spc https://spcjarfile.blob.core.windows.net/spcjar/spring-petclinic-3.2.0-SNAPSHOT.jar?sp=r&st=2024-03-27T10:19:06Z&se=2024-03-28T18:19:06Z&spr=https&sv=2022-11-02&sr=b&sig=ZXNXQMlCPf0aeMWLhsy%2FoCXR5L3muSsRxSvjW%2BQC56I%3D /spc/spring-petclinic-3.1.0-SNAPSHOT.jar
WORKDIR /spc
CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]
------------------------
# Difference between Copy and ADD

FROM tomcat:9-jdk8
LABEL author="ARIFULLA"
EXPOSE 8080
ADD https://spcjarfile.blob.core.windows.net/gameoflifewar/gameoflife.war /usr/local/tomcat/webapps/gameoflife.war

docker image build -t gol:1.0 .
docker image ls
docker container run -d -P --name gol gol:1.0 
docker container ls
<publicip>:port/gameoflife

cp Dockerfile mydockerfilegol
vi mydockerfilegol
<COPY ./gameoflife.war /usr/local/tomcat/webapps/gameoflife.war>
docker image build -f mydockerfilegol -t gol:2.0 .
docker container run -d -P --name golnew gol:2.0
http://20.244.29.245:32769/gameoflife/
git clean -fd .
-------------------------------------------

# Change the Docker Workdir usecase
FROM amazoncorretto:17-alpine3.17-jdk
LABEL author="Arifulla" 
LABEL project="SPCDummyProject"
ADD https://spcjarfile.blob.core.windows.net/spcjarfile/spring-petclinic-3.1.0-SNAPSHOT.jar /spc/spring-petclinic-3.1.0-SNAPSHOT.jar
WORKDIR /spc
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]

docker image build -t spc:1.0
docker container run -d -P --name spc spc:1.0
http://20.244.29.245:32774/

docker container exec sample1 whoami
docker container exec sample2 whoami
docker container exec sample3 whoami
docker container exec sample4 whoami
---------------------------------------------------------
# Change the Docker NonRoot user
----------------
cat Dockerfile

FROM amazoncorretto:17-alpine3.17-jdk
LABEL author="Arifulla" 
LABEL project="SPCDummyProject"
# creates a new group and user
RUN addgroup -g 1000 spc && adduser -h "/spc" -u 1000 -G spc -s /bin/bash -D spc
# switching to user spc
USER spc
# Download the file
ADD --chown=spc:spc https://spcjarfile.blob.core.windows.net/spcjarfile/spring-petclinic-3.1.0-SNAPSHOT.jar /spc/spring-petclinic-3.1.0-SNAPSHOT.jar
WORKDIR /spc
EXPOSE 8080
CMD ["java", "-jar", "spring-petclinic-3.1.0-SNAPSHOT.jar"]

#Commands
docker image build -t spc:nonroot .
docker image ls
docker container run -d -P --name spcnew spc:nonroot
docker container exec spcnew pwd
docker container exec spcnew whoami
-----------------





