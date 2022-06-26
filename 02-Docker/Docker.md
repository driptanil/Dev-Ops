 - Application are run on servers.
- Previously, 1 application on 1 server.
- If any wanted to make an application, they had to purchase a server
- VM-Ware solved the problem, which many application to run on servers.
- But virtual machine are very slow, as specific memory and storage had be allocated.
- Docker does need any Operating System and no operation.

#### Containers

- Containers does not need 

### Docker 
- Docker is an open platform for developing, shipping, and running applications. 
- Docker provides the ability to package and run an application in a loosely isolated environment called a container. 

##### Docker Runtime
- Runtime allows us to start or stop the containers.
- ###### Run C
	- `runc` is used to start or stop the containers.
- ###### Container D
	- `container d` is used to manage `runc` and also control how the container would interact with the internet.
- ###### Shim 
	- Once the container is created, `runc` will be removed, and for instance docker daemon is updated. Every container runs on docker daemon, therefore all running container will get stopped.
	- `shim` prevents this from happening, it is responsible for running of containers.

#### Commands

- `docker run <image>` will run the image and creates a new container, if the image is given, is not present locally. Then it will download the docker image from docker-hub registry.
  
- A docker images contains the operation system files and also the dependencies of the application file.
  
- `docker run -it <image>` will run the image in an interactive environment (does not exit).

- `docker pull <image>` will download the image from docker-hub registry.
  
- `docker images` displays all the images present locally.
  
- `ps aux` displays the processes in the system.
   
- `docker container ls` will list all the containers.
  
- `docker container exec -t <container_id> bash` will attach the terminal to a running container with given id.
  
- `docker stop <container_id>` will stop a running container with given id.
  
- `docker rm <container_id>` will remove the container with the given id.
  
- `docker log <contianer_id>` will display all the history of commands and their outputs.
  
- `docker prune -f` will delete all the local containers.
  
- `docker run -d <image>` will run the image in background (detached mode) .
  
- `docker ps` will display all the running containers. 
  
- `docker logs --since <time> <container_id>` 
  
- `docker stop <container_id>` will stop a running container.
  
- `docker run -p <port> <image>` will run the docker image in container on custom port.
  
- `docker start -it <container_id>` will start the existing container.
  
- `docker commit -m <commit_message> <container_id> <custom_container_name>:<version>` will save the container and display it in `docker images`. 
  
-  `docker images -q` will display all the container id of images
  
- `docker rmi $(docker images -q) -f` will force remove all the docker images.
  
- Docker images are made of layers.
	- For instance, image 1 uses some common files used by image 2. So downloading same files twice doesn't make sense. This is why images are divided into layer.
	- Therefore, if image 1 and image 2 have a common layer, then this layer is not downloaded twice.

```
╰─λ sudo docker run ubuntu:16.04  

	Unable to find image 'ubuntu:16.04' locally  
	16.04: Pulling from library/ubuntu  
	58690f9b18fc: Pull complete  
	b51569e7c507: Pull complete  
	da8ef40b9eca: Pull complete  
	fb15d46c38dc: Pull complete  
	Digest: sha256:20858ebbc96215d6c3c574f781133ebffdc7c18d98af4f294cc4c04871a6  
	fe61  
	Status: Downloaded newer image for ubuntu:16.04
```

- `docker images -q --no-trunc` will displays the hash value of all the docker image.

- `docker inspect <container_id>` displays information about the image in JSON format.
  
``` 
╰─λ sudo docker pull ubuntu  

	Using default tag: latest  
	latest: Pulling from library/ubuntu  
	125a6e411906: Already exists
```
-> layer already exists

#### Docker Config Files

```
╰─λ cat Dockerfile

	File: Dockerfile  
	FROM ubuntu  
	MAINTAINER driptanil datta <driprecovery@gmail.com>  
	RUN apt-get update  
	CMD ["echo","system updated"]
```

`docker build -t <custom_image_name> <directory>` to build a image from the docker config files.

```
╰─λ sudo docker built -t myimage:1.0 .
	
	Sending build context to Docker daemon  2.048kB  
	Step 1/4 : FROM ubuntu  
	---> d2e4e1f51132  
	Step 2/4 : MAINTAINER driptanil datta <driprecovery@gmail.com>  
	---> Running in 1264362e2047  
	Removing intermediate container 1264362e2047  
	---> 40f8b1bb0875  
	Step 3/4 : RUN apt-get update  
	---> Running in 41ca0f33d7df
	Reading package lists...  
	Removing intermediate container 41ca0f33d7df  
	---> 19c7fe42888d  
	Step 4/4 : CMD ["echo","system updated"]  
	---> Running in 3b9420da6c3d  
	Removing intermediate container 3b9420da6c3d  
	---> 9b27e3e08de9  
	Successfully built 9b27e3e08de9  
	Successfully tagged myimage:1.0
```


`docker run <images>` will run the docker image.

```
╰─λ sudo docker run myimage:1.0  
	
	system updated
```

### Docker Architecture

- Docker uses a client-server architecture.
![450](images/DockerArchitecture.png)

### Docker Daemon

- Docker daemon `dockerd` listens for requests of Docker API requests and manages Docker objects like images, container, networks and volumes.
  
### Docker Client

- Docker client `docker` is the primary way that many many Docker users interact with Docker.
  
### Docker Registry

- Docker registry stores Docker images. Docker Hub is public registry 
