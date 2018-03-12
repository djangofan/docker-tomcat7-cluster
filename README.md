# docker-tomcat7-cluster

A experiment running a docker cluster.  Runs 3 Tomcat machines and 1 NGinx machine in tandem.

https://tomcat.apache.org/tomcat-7.0-doc/cluster-howto.html

## Intentions

```
Round Robin, Not Sticky
Portainer 9000
NGinx 10080
Tomcat1 10081
Tomcat2 10082
Tomcat3 10083
Tomcat Internal Container Ports: 10080 + 10443 + 10009
80 - your local apache webserver on your computer
8080 - reserved. i avoid using it here
```

## Instructions

#### Run Portainer so you can view the docker config:

    docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer --no-auth

    http://192.168.99.100:9000/ or http://localhost:9000/


#### Start a Tomcat to test it.  The container should show up visible within Portainer:

    docker run -it --rm -p 8888:8080 tomcat:8.0

    docker run -d --rm -p 8888:8080 tomcat:8.0


#### Run the cluster defined in this project:

    docker-compose up
    
    http://192.168.99.100:10080/ or http://localhost:10080/



