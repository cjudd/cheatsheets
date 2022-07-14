# Docker Cheat Sheet

## Resources
* https://www.docker.com
* https://hub.docker.com
* https://dzone.com/refcardz/getting-started-with-docker-1
* https://dzone.com/articles/why-docker-is-not-yet-widely-successful-in-product
* https://jpetazzo.github.io/2013/10/16/configure-docker-bridge-network/
* http://www.slideshare.net/tarkasteve/developerweek-2015-docker-tutorial

## Docker

### docker's ip
```
 docker ip
```

### Show docker containers

#### running containers
```
docker ps
```
#### last run container
```
docker ps -l
```
#### all containers
```
docker ps -a
```

### search for container images
```
docker search <keyword>
```

### run containers
#### run docker container
```
docker run <image> <command>
```
example:
```
docker run ubuntu /bin/echo 'Hello World'
```

#### run container interactively
```
docker run -it <image>
```
example:
```
docker run -it ubuntu /bin/echo 'Hello World'
```

#### run container as deamon
```
docker run -d <image>
```
example:
```
docker run -d ubuntu:14.04 /bin/sh -c "while true; do echo hello world; sleep 1; done"
```

### run container and port mapping
```
docker run -it -p <ext port>:<internal port> <image>
```
example
```
docker run -it -p 80:80 nginx
```

### run container and map volume
```
docker run -it -v <host dir>:<container dir> <image>
```
example
```
docker run -it -v ~/devl/tmp/:/data kalilinux/kali-linux-docker bash
```

### stop container   
```
docker stop <container>
```

### connect to existing container
#### connect to existing container with command-line access
```
docker exec -it <container> bash
```

#### connect to existing container with root access
```
docker exec -it --user root <container> bash
```

### access logs
#### access container logs
```
docker logs <container>
```
#### tail container logs
```
docker logs -f <container>
```

### display container port mappings
```
docker port <container>
```

### get/pull image
```
docker pull <username>/<repository>:<tag>
```

### push image
```
docker push <username>/<repository>:<tag>
```

### view/inspect details in json
```
docker inspect <container>
```

### list local images
```
docker images
```

### view conatiner layers
```
docker history <container>
```

### list process running in container
```
docker top <container>
```

### build a Dockerfile
```
docker build -t <image name> .
```

### backup container
#### export container
```
docker export <container> > <filename>.tar
```
#### import container
```
docker import <filename.tar> <image name>
```

### backup images
#### save image
```
docker save <image>
```
#### load image
```
docker load  < <filename.tar>
```

### time drift
```
docker-machine ssh default 'sudo ntpclient -s -h pool.ntp.org'
```

### networking
```
docker network ls
docker network create <network name>
docker run --network <network name> <image> <command>
docker network connect <network name> <container name>
```

## Examples
### Java Examples
#### Java Shell (Java 9)
```
docker run -it java:9 jshell
```
#### Java 8
```
docker run -it --rm dockerfile/java:oracle-java8 java -version
```
#### jcurl
```
docker run -it --rm javajudd/jcurl java -Djavax.net.debug=all -jar jcurl.jar https://www.grc.com
```

### memcached
```
docker run --name memcache -p 11211:11211 -d memcached
```

### mysql
```
docker run --name <name> -e MYSQL_ROOT_PASSWORD=root+1 -e MYSQL_DATABASE=<db> -e MYSQL_USER=<user> -e MYSQL_PASSWORD=<password> -p 3306:3306 -d mysql:latest
```
```
docker run --name mysql -e MYSQL_ROOT_PASSWORD=root+1 -p 3306:3306 -d mysql:5.5.44
```
### Ultimate Enterprise Java Build System
#### Jenkins - https://hub.docker.com/_/jenkins/
```
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins -v /var/jenkins_home jenkins
```
#### Nexus - https://hub.docker.com/r/sonatype/nexus/
```
docker run -d -p 8081:8081 --name nexus -v /sonatype-work sonatype/nexus
```
#### Postgres - https://hub.docker.com/_/postgres/
```
docker run -d --name sonar-postgres -v /var/lib/postgresql/data -e POSTGRES_USER=sonar -e POSTGRES_PASSWORD=sonar -e POSTGRES_DB=sonar postgres
```
#### Sonarqube - https://hub.docker.com/_/sonarqube/
```
docker run -d --name sonarqube \
    -v /opt/sonarqube \
    --link sonar-postgres:db \
    -p 9000:9000 -p 9092:9092 \
    -e SONARQUBE_JDBC_USERNAME=sonar \
    -e SONARQUBE_JDBC_PASSWORD=sonar \
    -e SONARQUBE_JDBC_URL=jdbc:postgresql://db/sonar \
    sonarqube
```
### create files/pdfs
```
docker run -it --rm  -v $(pwd):/work mnuessler/pdftk $(for i in $(seq 1 40); do echo -n "1_MB.pdf "; done) cat output 40.pdf
```
### portero
```
docker run -p 9000:9000 -d --name portero javajudd/portero
```
### iis
```
docker run -d -p 8000:8000 --name my-site microsoft/iis
```
### wordyninablog
```
docker run --name wordyninjadb -e MYSQL_ROOT_PASSWORD=root+1 -e MYSQL_DATABASE=wordyninjadb -e MYSQL_USER=wordyninja -e MYSQL_PASSWORD=password+1 -p 3306:3306 -d mysql:latest
```

### mailtrap
https://hub.docker.com/r/eaudeweb/mailtrap/
```
docker run -d --name=mailtrap -p 80:80 eaudeweb/mailtrap
```

## Docker Machine

### create
#### create local docker machine
```
docker-machine create -d virtualbox <machine_name>
```
#### create AWS docker machine
```
docker-machine -D create \
    --driver amazonec2 \
    --amazonec2-access-key <aws-access-key> \
    --amazonec2-secret-key <aws-secret-key> \
    --amazonec2-region <aws-region> \
    --amazonec2-vpc-id <aws-vpc> \
    --amazonec2-zone <aws-zone> \
    <machine-name>
```
#### create DigitalOcean docker machine
```
docker-machine create --driver digitalocean --digitalocean-access-token <digitalocean-token> <machine-name>
```

### remove docker machine
```
docker-machine rm <machine-name>
```

### list docker machines
```
docker-machine ls
```

### switch machines
```
docker-machine env <machine-name>
eval "$(docker-machine env <machine-name>)"
```

### port forwarding
#### enabled port forwarding
```
VBoxManage controlvm "<docker-machine name>" natpf1 "<descriptive name of port>,tcp,,<host port>,,<guest port>"
```
example
```
VBoxManage controlvm "iq" natpf1 "iq-tcp-port,tcp,,9090,,9090"
```

#### disable port forwarding
```
VBoxManage controlvm "<docker-machine name>" natpf1 delete "<descriptive name of port>"
```
example
```
VBoxManage controlvm "iq" natpf1 delete "iq-tcp-port"
```
