![](images/kubernetes-cover.png)
# Configuration Management

- It helps to maintain infrastructure using software (like providing resources)
  
- immutability of configuration of container which runtime.
  
  (like update an application, start a new container for the new version and stop the previous container)
  
- when services require some dependencies, then containers(docker) are used.
  
- eg Chef, Puppet

## Managing Containers 

- For example, a website contains frontend, backend, database and networking components.
  
- **Monolithic Applications**: 
	- When all components of the website are bundled together and are running as a single application
	  
	- Changes in a single component, would require the whole bundled to be re-deployed (not efficient).
	  
- **Micro-Services**:
	- Here all components of a website are deployed individually which is called a micro-service.
	  
	- Changes in an individual component can be re-deployed individually (much more efficient).
	  
	- Fault-Isolation and debugging become easier

# Kubernetes (k8s)

- It is an open-source container orchestration tool, developed by Google and donated to CNCF (Cloud Native Computing Foundation).
  
- It helps in managing containerized applications in different deployment environments.
  
- Applications which follow all the principles and applications that can run on top of Kubernetes are called **Cloud-Native Applications**.

##### Need for container orchestration tool

- Over the years, there is an increase in micro-services and containers.
  
- deploying and managing multiple containers dynamically 
  
  (before using only scripts was becoming complex)

##### Features of container orchestration tool

- **High Availability** or no downtime
- **Scalability** or high performance
- **Disaster recovery** - backup and restore

## Architecture


- K8s Cluster = Control Plane + Nodes
  ![](https://miro.medium.com/max/1400/1*kSRH4T8S1YmAuHbpgQ3Ylw.png)

- single **Control Plane** (Master Node):
	- It is a collection of various components which helps in managing the health of the overall cluster.
	  
	- runs several processes that necessary to run and manage the cluster 
	  properly
	  
	- **API server** is the front end for the Kubernetes control plane. 
	  (entry point of K8s cluster and is responsible for all communications)
	  (listens to HTTPS port: 443 for requests)
	  
	  - API: An application programming interface is a way for two or more computer programs to communicate with each other.
	    
	- **Controller Manager** (ensures proper working of the containers) 
	  
	  functions: desired state, current state, differences, making changes
	  
		- using "Kubectl" which is K8s CLI, it communicates with API server for execution (imperative way)
		  
		- using manifest files present in worker nodes like .yaml files (declarative way)
		  
	- **Scheduler** (responsible for scheduling containers in nodes based on workloads, it listens to the API server)
	  
	- **ECTD key value storage** (it holds current state of K8s cluster, configuration data of each node and takes snapshots for backup and restoration)
	  
	  - Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data
	    
- multiple **Data Plane** (Worker Nodes):
	- **'Kubelet'** process running, makes sure that containers are running in a Pod.
	   (for communication with the API server and execute some tasks)
	   
	- **'Kube-Proxy'** is responsible for networking and provides IP addresses to nodes.
	   
	- Worker Node -> Container Runtime -> Pod -> Container
	  
	- **Pod** is the smallest execution unit and containers in the same pod share their lifecycle and storage resources. 
	  
- **Virtual Network**:
	- it unifies all the nodes inside of a cluster into a power machine (which is a sum of all resources of all the individual worker nodes)

### Steps to run an application on K8s

1. Divide the Application to create multiple microservices
2. Add each microservice to each container
3. Put container in Pods
4. Deploy the Pods to the controller

##### Commands :
- Kubectl 
	- `kubectl version` -> prints version details
	- `kubctl version --output=yaml` ->prints yaml output of version details 
	- `kubctl get pods` -> prints details of running nodes
	- `kubectl get nodes`
	- `kubectl get`
	- `kubectl config` 
	- `kubectl config current-context`
	- `kubectl get all`
	- `kubectl delete pod <name>`

- Minikube
	- `minikube start` -> will create a single node cluster
	- `minikube stop` 
	- `minikube remove`
	- `minikube status`
	- `minikube dashboard` -> opens the dashboard in localhost
	- `minikube docker-env` -> prints the environment variable for docker
	- `minikube ssh` -> open minikube in secure shell