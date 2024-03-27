
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
