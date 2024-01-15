---
title: "Docker"
datePublished: Mon Dec 11 2023 17:58:05 GMT+0000 (Coordinated Universal Time)
cuid: clq17vm3s000808jtcompdbxs
slug: docker
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/HSACbYjZsqQ/upload/26920e5fbb4bf3b60ffb63a8bd565ea7.jpeg
tags: docker, docker-network, docker-bridge-network, docker-overlay-network, macvlan

---

* Docker is an open-source centralized platform designed to create and run applications.
    
* Docker uses container on the host OS to run applications. It allows applications to use the same Linux kernel as a system on the host computer, rather than creating a whole virtual OS.
    
* We can install docker on any OS but Docker engine run natively on Linux distribution.
    
* Docker is written in go language.
    
* Docker is a tool that performs OS level virtualization also known as containerization.
    
* Before Docker, many users face the problem that a particular code is running in developer’s system but not in user’s system.
    
* Docker was first released in march 2003. It was founded by Solomen hykes, SebastienPahl and Kamel Founadi.
    
* Docker is a set of platform as a service that use OS Level virtualization to deliver software in packages called containers.
    

### Docker Components

*Docker Daemon*

* Docker daemon runs on the host OS.
    
* It is responsible for running containers to manage docker services.
    
* Docker Daemon can communicate with other daemons.
    

### *Docker client*

* Docker users can interact with docker daemon through a client (CLI).
    
* Docker client uses command (CLI) and Rest API to Communicate with the Docker Daemon.
    
* When a client runs any server command on the docker client terminal , the client terminal sends the docker commands to the Docker Daemon .
    
* It is possible for docker client to communicate with more than none Daemon.
    

### *Docker host*

* Docker Host is used to provide an environment to execute and run applications.
    
* It contains the Docker Daemon , images containers, networks and storages.
    

### *Docker Hub / Registry*

Docker registry manages and stores the docker Images. There are two types of registries in the docker.

1. Public Registry :- Public registry is also called as docker hub.
    
2. Private Registry :- It is used to share images with in the enterprise.
    

### *Docker Images*

> Docker images are the read only binary templates used to create docker containers.

`or`

> Single file with all dependencies and configuration required to run a program.

*Ways to create an Images*

1. Take image from Docker Hub.
    
2. Create image from Docker file.
    
3. Create image from existing Docker Containers.
    

### *Docker Container*

* Container hold the entire packages that is needed to run the application. In other words , we can say that , the image is a template and the container is a copy of that template.
    
* Containers is like a virtual machine.
    
* Images became container when they run on Docker engine.
    

```yaml
yum install docker -y
docker images
docker ps
docker ps -a
docker pull
docker run -it --name <container name> ubuntu /bin/bash
service docker status
docker start <container_name>
docker stop <container_nmae>
docker attach <container_nmae>
docker exec <container_nmae>
docker rm <container_nmae>
```

### Docker Networking

when you install docker, it creates 3 networks automatically.

1. bridge
    
2. none
    
3. host
    

### bridge:

bridge is a private internal network created by docker in the host.

All the containers are attached to this network by default and gets an Private IP address in the range of 172.17.series. All containers can access each other by using this IP address.

To access any container from outside you need to map the port of these containers to host.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705242890846/fe0846e5-37fd-46a1-ac3a-1996913a15a2.png align="center")

### Overlay Network:

Overlay network driver creates a distributed network among multiple Docker daemon hosts. This network sits on top of (overlays) the host-specific networks, allowing containers connected to it (including swarm service containers) to communicate securely when encryption is enabled.

when you initialize a swarm or join a docker host to an existing swarm 2 networks get created by default.

1. an overlay network called ingress, which handles the control and data traffic related to swarm services. When you create a swarm service and do not connect it to a user-defined overlay network, it connects to the ingress network by default.
    

#### Ingress Network

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705322398247/9d55dcf2-c66a-499f-be45-7b0b791e7621.png align="center")

Ingress network has built-in load balancer that redirects traffic from published to all the mapped ports.  
Ingress network created automatically so no configuration needed.

1. a bridge network called docker\_gwbridge, which connects the individual Docker daemon to the other daemons participating in the swarm.
    
### macvlan
macvlan network driver can be used to assign a MAC address to each container's virtual network interface, making it appear to be a physical network interface directly connected to the physical network.

#### Routing Mesh

Routing mesh is just a way of saying "Allow this service to be reachable on any node". With routing mesh, the request can hit any swarm member and still get services by the node that runs the service.

Docker Engine Swarm mode makes it easy to publish ports for services to make them available to resources outside the swarm. All nodes participate in an ingress routing mesh. The routing mesh enables each node in the swarm to accept connections on published ports for any service running in the swarm, even if there is no task running on the node. The routing mesh routes all incoming requests to published ports on available nodes to an active container.