<h2>Docker </h2>


Containers Terms: Container runtime, Container layers, Container registry (remote hub for all containers)

<h3>Container</h3>
A container is a unit of software/ deployment that contains code, runtime, system tools, system libraries.
Container is, 
<ul>
	<li>compatible with any Linux distribution</li>
	<li>light-weight (order of KB)</li>
	<li>move faster by deploying smaller units.</li>
	<li>able to replicate easily.</li>
	<li>uses few resources.</li>
	<li>share the same OS kernel, thus quick to start (doesn’t have to boot) less. isolation and fit more.</li>
	<li>It stays alive, till the process inside is alive. Thus, ideal for short lived tasks.</li>
</ul>


<h3>Docker</h3>

Provides a container runtime (eg. Docker desktop) and command line tool to create and manage containers. 
Software containerization to reduce time and cost

Faster in development and deployment
<ol>
	<li>Consistency across all devices</li>
	<li>Isolation: security and debugging</li>
	<li>Version control</li>
	<li>Scalability</li>
	<li>Dev op integration</li>
</ol>


<h3>Images and containers</h3>
<ol>
	<li>Lightweight</li>
	<li>Standalone</li>
	<li>Executable package</li>
</ol>


To run a software

Volumes (** need to practice more)
–	Containers are ephemerous (short-lived) so does the data, to save the data, we map the volume to a folder on the host to a logical folder in the container ie. persistent data container (data durability)

1.	Client (instructions)
2.	Host (managing containers)
3.	Registry (centralised storage and distribution of repository of images)

Commands
<ol>
	<li>EXPOSE</li>
	<li>ARG</li>
	<li>VOLUME</li>
	<li>CMD</li>
	<li>ENTRYPOINT (CMD)</li>
</ol>


Docker file is the blueprint of the docker image. It defines the environment i.e steps to build a docker image, and this file is immutable. Helps the app to run as a container.

Docker image is the template to run the docker container. Images are fetched from local cache, if not found locally, it fetches from the remote repository docker hub

Docker Container is the running process. One docker image can spawn into multiple running containers and Kubernetes helps to scale this.

Containers are isolated environments, having their own processes, services, networks and volumes. 



<h4>Container registry </h4>

Two modes in docker:
<ol>
    <li>Interactive </li>
    <li>Detached (containers that runs in background of your terminal) </li>
</ol>

Data persistence:
<ul>
    <li>When a database container is deleted, the data will be erased. So, we need to map to a directory outside the container. </li>
    <li>docker run -v /<outside directory>:/<container directory> <container name> </li>
</ul>


Image name: the images you find in the container registry 


Info	get all info about the docker, version, images, containers count etc	



```
docker info
```

	docker version	
 ```
 docker version
```
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
