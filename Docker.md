Table of Contents
Containers	1
YAML (Yet Another Markup Language)	1
Docker	2
Kubernetes (K8S)	6
Helm charts:	8

Containers
Terms:
Container runtime, Container layers, Container registry (remote hub for all containers)

A container is a unit of software/ deployment that contains code, runtime, system tools, system libraries.

Container is, 
•	compatible with any Linux distribution
•	light-weight (order of KB)
•	move faster by deploying smaller units.
•	able to replicate easily.
•	uses few resources.
•	share the same OS kernel, thus quick to start (doesn’t have to boot) less. isolation and fit more.
•	It stays alive, till the process inside is alive. Thus, ideal for short lived tasks.


YAML (Yet Another Markup Language)

• often used configuration format.
• provides data in human-readable format.
• used for object serializable
3.1 File initialization
It starts with three dashes(-), indicates the start of the file.
---
3.2 Data Types and Representation
- Data is represented in key-value pairs.
- key is always a string and the value is a scalar, can be of any data type.
- Supports four Data types:
1. String: declared with singel quotes(’) or double quotes(”) or no quotes.
2. boolean: true or false
3. floating-point number: eg. 3.1243
4. array: each item is denoted by an indentation of two spaces.
5. dictionary: collection of different data types.
"myDict": {
"item1": "string value",
"item2": false,
"item3": [
"arr-item1": item1,
"arr-item2": item2
]
}
whitespace are used for formatting and it forbids tabs
newline indicate next line i.e the end of a field.
3.3 Comments
Represented by a # symbol.
They take up the whole line or placed at the end of the field

Docker

-	Provides a container runtime (eg. Docker desktop) and command line tool to create and manage containers. 
Software containerization to reduce time and cost

Faster in development and deployment
1.	Consistency across all devices
2.	Isolation: security and debugging
3.	Version control
4.	Scalability
5.	Dev op integration


Lightweight


Images and containers

1.	Lightweight
2.	Standalone
3.	Executable package

To run a software

Volumes (** need to practice more)
–	Containers are ephemerous (short-lived) so does the data, to save the data, we map the volume to a folder on the host to a logical folder in the container ie. persistent data container (data durability)

1.	Client (instructions)
2.	Host (managing containers)
3.	Registry (centralised storage and distribution of repository of images)

Commands
1.	EXPOSE
2.	ARG
3.	VOLUME
4.	CMD
5.	ENTRYPOINT (CMD)


Docker file is the blueprint of the docker image. It defines the environment i.e steps to build a docker image, and this file is immutable. Helps the app to run as a container.

Docker image is the template to run the docker container. Images are fetched from local cache, if not found locally, it fetches from the remote repository docker hub

Docker Container is the running process. One docker image can spawn into multiple running containers and Kubernetes helps to scale this.

Containers are isolated environments, having their own processes, services, networks and volumes. 



<h4>Container registry </h4>

Two modes in docker:
<ol>
    <li>Interactive </li>
    <li>Detached (containers that runs in background of your terminal) </li>

Data persistence:
<ul>
    <li>When a database container is deleted, the data will be erased. So, we need to map to a directory outside the container. </li>
    <li>docker run -v /<outside directory>:/<container directory> <container name> </li>



Image name: the images you find in the container registry 

	Description	command
Info	get all info about the docker, version, images, containers count etc	docker info
	docker version	docker version
Images		
	List all the docker images	docker images
	Remove a docker image (make sure no container is running from this image: stop and delete them)	docker rmi <image name>
	To pull an image from registry	docker pull <image name>
	pull image with a tag	docker pull <image name>:<version>
	get image info	docker image inspect <image name>
	remove all images that are not in use by any container	docker system prune -a
Containers		
	List all running containers	docker ps -a
	get list of all container ids	docker ps -a -q
	To run a container from an image	docker run <container name> <image name>
	to publish a port for a container (--publish or -p)	docker run --publish [or -p] <host port>: <container_port>
	to run an interactive cmd (it attaches the container terminal)	docker run -it <application>
	Start a container	docker start <container name/id>
	Stop a running container	docker stop <container name/id>
	Kill a container	docker kill <container>
	Remove a container permanently (only stopped ones)	docker rm <container name/id>
	To remove a running container	docker rm -f <container name/id>

	inspect container env variables	docker inspect <container name>
	set max memory for a container	docker run -–memory=”256m” <container name>
	set max CPU for the container	docker run –cpus=”.5” <container>
	attach to the container	docker container exec -it <container name> <program name>
Volumes		
	List all volumes	docker volume ls
	Remove a volume	docker volume rm <volume name>
Networking		
	Run a container with port mapping	docker run --name <container name> -p <host port>:<container port> <image name>
	List all networks	docker network ls	
	Inspect details of the network	docker network inspect <network name>
	Define a user-defined bridge	docker network create <new network name>
	Connect a container to a network	docker network connect <network name> <container name>
	disconnect a container to a network	docker network disconnect <network name> <container name>



docker kill "$(docker ps -q --filter name=ccaas)"
docker rm -f
docker image rm -f
docker images -aq –filter reference=’give ref*’
 
docker run –rm (-v) hyperledger/fabric-tools
docker -f compose/
 


docker exec cli ./scripts/setAnchorPeer.sh $ORG $CHANNEL_NAME

docker build -f $CC_SRC_PATH/Dockerfile -t ${CC_NAME}_ccaas_image:latest --build-arg CC_SERVER_PORT=9999 $CC_SRC_PATH >&log.txt


docker run --rm -d --name peer0org1_${CC_NAME}_ccaas  \
                  --network fabric_test \
                  -e CHAINCODE_SERVER_ADDRESS=0.0.0.0:${CCAAS_SERVER_PORT} \
                  -e CHAINCODE_ID=$PACKAGE_ID -e CORE_CHAINCODE_ID_NAME=$PACKAGE_ID \
                    ${CC_NAME}_ccaas_image:latest


Docker exec command: to execute the command in a container OS.


Adding tag to tell the version

docker run redis => gives the latest version
docker run redis:4.0 => gives the version 4.0


doesn’t read the input from console


Docker Compose is a tool for defining and running multi-container applications. It is the key to unlocking a streamlined and efficient development and deployment experience.
Compose simplifies the control of your entire application stack, making it easy to manage services, networks, and volumes in a single, comprehensible YAML configuration file. Then, with a single command, you create and start all the services from your configuration file.

**commands handson

 
Kubernetes (K8S)
Supports Docker, CRI-O, containerd

-	Automatic deployment of containers for a defined image across different work stations and servers
-	Distribution of the load across multiple servers
-	Auto-scaling of the deployed application
-	Monitoring and health-checks of the container
-	Replacement of the failed container.
-	Automated rollouts and rollbacks

Deployment of the containerization in the production. Manage the containers.

Tool that handle the workload

Node – kubelet (Ensures that containers are running in a Pod by interacting with the Docker engine, the default program for creating and managing containers. Takes a set of provided PodSpecs and ensures that their corresponding containers are fully operational. )
Node contains pods
Define objects in yaml

Two types of nodes:
1.	Master node (api server, controller manager, scheduler)
2.	Worker nodes

Master node (Control plane)
1.	API server
a.	REST interface
b.	Save state to the datastore (etcd)
c.	All clients interact with it, never directly to the datastore
2.	Etcd
a.	Key-value store
b.	Act as the cluster data stor for storing state
3.	Control manager
a.	To run other controllers like node, replication, endpoints 
4.	Cloud manager
5.	Scheduler
a.	Assigns nodes to the pods
b.	Checks for resource requirements

Node (form a cluster)

Worker node:
1.	Multiple pods
2.	Kube-proxy (service)
a.	Manages networks
3.	Kubelet (service) 
a.	Manages the pods lifecycle
b.	Health montoring of the pods
4.	Container runtime (service)

Pod 
-	smallest unit in K8S, Pod run in a node
-	encapsulates an application’s container
-	can run one or multiple containers
-	Containers (containers run in Pod), Share mounted volumes, Share IP address
-	Within the Pod the communication happens through local host, IPC
-	If a Pod fails, it is replaced with a new one
-	Pod are not updated, they are replaced with an updated version.
-	Scale by adding more pods, not by increasing containers in pods
-	If there are more than one container, then among them one will be the main worker which contains all the logic and the rest will be the side supporters.


One pod => one server.

Pod lifecycle:
1.	Creation (API server -> etcd -> scheduler -> Kubelet -> Runtime -> update in etcd)
2.	Deletion (API server -> etcd (grace period) -> Kubelet -> Runtime controller)
3.	Pod state(tells where it is in the life cycle)
1.	Pending
2.	Running
3.	Succeeded
4.	Failed
5.	Unknown (communication issues)


Example:
kubectl run nginx --image=mynginx1
kubectl get pods
kubectl describe pod mynginx1
kubectl delete pod mynginx1-794574cd66-799zk

kubectl get pods -o wide (gives ip address and assigned node)

Container states:
1.	Waiting
2.	Running
3.	terminated

kubectl is the CLI
-	it communicates with the API server
-	configuration stored locally
o	${HOME}/.kube/config

Calico implements the Kubernetes Container Network Interface (CNI) as a plug-in and provides agents for Kubernetes to provide networking for containers and pods.

		
	get all the nodes in the cluster	kubectl get nodes
	cluster info (gives the url)	kubectl cluster-info
	running server version	kubectl version
	cluster configuration	kubectl config view
	client version	kubectl version –client
	check the name of the container runtime	kubectl get nodes -o wide
	list all pods	kubectl get pods
	filter by namespace	kubectl get pods -n <namespace>
	all the data	kubectl describe node


Context: (** handson)
Contains a cluster, a user and a namespace.

Contexts are shortcuts that let you quickly switch between different cluster configurations without typing long and tedious commands.
Context details are stored in kubeconfig file - a YAML configuration file used by Kubernetes to authenticate and connect to the Kubernetes API server.

**Command to create cluster?

kubectl create deployment mynginx1 --image=nginx

kubectl create -f “myfilename.yaml”


Namespaces:
-	Allows to group resources
-	Deleting a namespace will delete all its child objects

kubectl get ns 
kubectl create/delete ns [namespace name]
 


 
Helm charts:
-	Provides a better way to manage all the Kubernetes YAML files we create on Kubernetes projects.



CI/CD techniques
 
sudo yum -y update

sudo yum -y install epel-release

sudo yum -y install libvirt qemu-kvm virt-install virt-top libguestfs-tools bridge-utils
 
Doubts:

How to know which YAML file is running, is it from docker or Kubernetes?

