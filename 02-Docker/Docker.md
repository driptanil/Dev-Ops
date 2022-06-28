# Introduction
- Application are run on servers.
- Previously, 1 application on 1 server.
- If any wanted to make an application, they had to purchase a server
- VM-Ware solved the problem, which many application to run on servers.
- But virtual machine are very slow, as specific memory and storage had be allocated.
- Docker does need any Operating System and no operation.

#### Containers

- Containers provide a way of creating an isolated environment, sometimes called a sandbox, in which applications and their dependencies can live.

##### Why are containers useful?

**Portability** – the isolated environment that containers provide effectively means the container is decoupled from the environment in which they run. Basically, they don’t care much about the environment in which they run, which means they can be run in many different environments with different operating systems and hardware platforms.

**Consistency** – since the containers are decoupled from the environment in which they run, you can be sure that they operate the same, regardless of where they are deployed. The isolated environment that they provide is the same across different deployment environments.

**Speed to deploy** – for the same reasons as above. There is no need for considerations around how the application will operate in a production environment. If it runs in a container in one environment (say, your local machine), then it can be made to run in a container in another environment (say, in a cloud provider) very quickly

# Docker 
- Docker is an open platform for developing, shipping, and running applications. 
- Docker provides the ability to package and run an application in a loosely isolated environment called a container. 

Docker _(list of instructions)_ -> Image _(class)_ -> Container _(object)_

### Docker Runtime
- Runtime allows us to start or stop the containers.
- #### Run C
	- `runc` is used to start or stop the containers.
- #### Container D
	- `container d` is used to manage `runc` and also control how the container would interact with the internet.
- #### Shim 
	- Once the container is created, `runc` will be removed, and for instance docker daemon is updated. Every container runs on docker daemon, therefore all running container will get stopped.
	- `shim` prevents this from happening, it is responsible for running of containers.

### **Open Container Initiative (OCI)?**

- The **Open Container Initiative** (**OCI**) is a Linux Foundation project to design open standards for containers.
  
- Established in June 2015 by Docker and other leaders in the container industry.
  
- OCI currently contains two specifications: the Runtime Specification (runtime-spec) and the Image Specification (image-spec).
  
- OCI runtime spec defines how to run the OCI image bundle as a container.
  
- OCI image spec defines how to create an OCI Image, which includes an [image manifest](https://github.com/opencontainers/image-spec/blob/master/manifest.md), a [filesystem (layer) serialization](https://github.com/opencontainers/image-spec/blob/master/layer.md), and an [image configuration](https://github.com/opencontainers/image-spec/blob/master/config.md).

## Commands

- `docker run <image>` will run the image and creates a new container, if the image is given, is not present locally. Then it will download the docker image from docker-hub registry.
![650](images/hello-world.png)
  
- A docker images contains the operation system files and also the dependencies of the application file.
  
- `docker run -it <image>` will run the image in an interactive environment (does not exit).
  ![650](images/dockerrun-it.png)
 
- `docker images` displays all the images present locally.
  ![650](images/dockerimages.png)

- `docker pull <image>` will download the image from docker-hub registry.
  ![650](images/dockerpull.png)

- `ps aux` displays the processes in the system.
  ![650](images/psaux.png)
  
- `docker container ls` will list all the containers.
  ![650](images/dockercontainerls.png)
  
- `docker container exec -it <container_id> bash` will attach the terminal to a running container with given id.
  ![650](images/dockercontainerexec-it.png)
  
- `docker stop <container_id>` will stop a running container with given id.
  ![650](images/dockerstop.png)
  
- `docker rm <container_id>` will remove the container with the given id.
  ![650](images/dockerrm.png)
  
- `docker logs <contianer_id>` will display all the history of commands and their outputs.
  ![650](images/dockerlogs.png)
  
- `docker container prune -f` will delete all the stopped containers.
  ![650](images/dockercontainerprune-f.png)

- `docker run -d <image>` will run the image in background (detached mode).
  ![650](images/dockerrun-d.png)
  
- `docker ps` will display all the running containers. 
  ![650](images/dockerps.png)

- `docker ps -a` will display both running and stopped containers.
  ![650](images/dockerps-a.png)

- `docker logs --since <time> <container_id>`
  ![650](images/dockerlogs--since.png) 
  
- `docker stop <container_id>` will stop a running container.
  ![650](images/dockerstop.png)
  
- `docker run -p <port> <image>` will run the docker image in container on custom port.
![650](images/dockerrun-d-p.png)
  ![650](images/dockerrun-p.png)
  
- `docker start <container_id>` will start a stopped container.
  ![650](images/dockerstart.png)
- `docker commit -m <commit_message> <container_id> <custom_container_name>:<version>` will save the container and display it in `docker images`.
  ![650](images/dockercommit-m.png) 
  
- `docker images -q` will only display all the container id of images.
  ![650](images/dockerimages-q.png)

- `docker rmi <docker_image_id> -f` will force remove the docker image.
  ![650](images/dockerrmi-f.png)
  
- `docker rmi $(docker images -q) -f` will force remove all the docker images.
  ![650](images/dockerrmi$(dockerimages-q)-f.png)
  
- Docker images are made of layers.
	- For instance, image 1 uses some common files used by image 2. So downloading same files twice doesn't make sense. This is why images are divided into layer.
	- Therefore, if image 1 and image 2 have a common layer, then this layer is not downloaded twice.

- `docker images -q --no-trunc` will displays the hash value of all the docker image.
  ![650](images/dockerimages-q--no-trunc.png)

- `docker inspect <container_id>` displays information about the image in JSON format.
  ![650](images/dockerinspect.png)
  
``` 
╰─λ sudo docker pull ubuntu  

	Using default tag: latest  
	latest: Pulling from library/ubuntu  
	125a6e411906: Already exists
```
-> layer already exists

- `docker login` for login in command line interface.
![650](images/dockerlogin.png)
  
### Docker Config Files

![650](images/catdockerfile.png)

- `docker build -t <custom_image_name> <directory>` to build a image from the docker config files.
![650](images/dockerbuild-t.png)

- `docker run <images>` will run the docker image.
![650](images/dockerruncustom.png)

### Docker Architecture
- Docker uses a client-server architecture.
![550](images/DockerArchitecture.png)

### Docker Daemon
- Docker daemon `dockerd` listens for requests of Docker API requests and manages Docker objects like images, container, networks and volumes.
  
### Docker Client
- Docker client `docker` is the primary way that many many Docker users interact with Docker.
  
### Docker Registry
- Docker registry stores Docker images. Docker Hub is public registry 
