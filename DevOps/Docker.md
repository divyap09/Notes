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

<table>
	<thead>
		<tr>
			<td></td>
			<td>Description</td>
			<td>Command</td>
		</tr>
	</thead>
	<tr>
		<td>Info</td>
		<td>get all info about the docker, version, images, containers count etc</td>
		<td><code>docker info</code></td>
	</tr>
	<tr>
		<td></td>
		<td>docker version</td>
		<td><code>docker version</code></td>
	</tr>
	<tr>
		<td>Images</td>
		<td>List all the docker images</td>
		<td><code>docker images</code></td>
	</tr>
	<tr>
		<td></td>
		<td>Remove a docker image <br/> (make sure no container is running from this image: stop and delete them)</td>
		<td><code>docker rmi &lt;image name&gt;</code></td>
	</tr>
	<tr>
		<td></td>
		<td>To pull an image from registry</td>
		<td><code>docker pull &lt;image name&gt; </code></td>
	</tr>
	<tr>
		<td></td>
		<td>pull image with a tag</td>
		<td><code>docker pull &lt;image name&gt;:&lt;version&gt;</code></td>
	</tr>
	<tr>
		<td></td>
		<td>get image info</td>
		<td><code>docker image inspect &lt;image name&gt;</code></td>
	</tr>
	<tr>
		<td></td>
		<td>remove all images that are not in use by any container</td>
		<td><code>docker system prune -a</td>
	</tr>
 	<tr>
		<td>Containers</td>
		<td>List all running containers</td>
		<td><code>docker ps -a</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>get list of all container ids	</td>
		<td><code>docker ps -a -q</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>To run a container from an image</td>
		<td><code>docker run &lt;container name&gt; &lt;image name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>to publish a port for a container (--publish or -p)</td>
		<td><code>docker run --publish [or -p] &lt;host port&gt;: &lt;container_port&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>to run an interactive cmd (it attaches the container terminal)</td>
		<td><code>docker run -it &lt;application&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Start a container</td>
		<td><code>docker start &lt;container name/id&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Stop a running container</td>
		<td><code>docker stop &lt;container name/id&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Kill a container</td>
		<td><code>docker kill &lt;container&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Remove a container permanently (only stopped ones)</td>
		<td><code>docker rm &lt;container name/id&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>To remove a running container</td>
		<td><code>docker rm -f &lt;container name/id&gt;</code></td>
	</tr>
	<tr>
		<td></td>
		<td>To check logs of a container</td>
		<td><code>docker logs -f &lt;container name/id&gt; </code></td>
 	<tr>
		<td></td>
		<td>inspect container env variables</td>
		<td><code>docker inspect &lt;container name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>set max memory for a container</td>
		<td><code>docker run -–memory=”256m” &lt;container name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>set max CPU for the container</td>
		<td><code>docker run –cpus=”.5” &lt;container&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>attach to the container</td>
		<td><code>docker container exec -it &lt;container name&gt; &lt;program name&gt;</code></td>
	</tr>
 	<tr>
		<td>Volumes	</td>
		<td>List all volumes</td>
		<td><code>docker volume ls</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Create a volume</td>
		<td><code>docker volume create &lt;volume name&gt;</code></td>
	</tr>	
 	<tr>
		<td></td>
		<td>Remove a volume</td>
		<td><code>docker volume rm &lt;volume name&gt;</code></td>
	</tr>
 	<tr>
		<td>Networking</td>
		<td>Run a container with port mapping</td>
		<td><code>docker run --name &lt;container name&gt; -p &lt;host port&gt;:&lt;container port&gt; &lt;image name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>List all networks</td>
		<td><code>docker network ls</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Inspect details of the network</td>
		<td><code>docker network inspect &lt;network name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Define a user-defined bridge</td>
		<td><code>docker network create <new network name></code></td>
	</tr>
 	<tr>
		<td></td>
		<td>Connect a container to a network</td>
		<td><code>docker network connect &lt;network name&gt; &lt;container name&gt;</code></td>
	</tr>
 	<tr>
		<td></td>
		<td>disconnect a container to a network</td>
		<td><code>docker network disconnect &lt;network name&gt; &lt;container name&gt;</code></td>
	</tr>
</table>





Docker exec command: to execute the command in a container OS.


Adding tag to tell the version

docker run redis => gives the latest version
docker run redis:4.0 => gives the version 4.0


doesn’t read the input from console


Docker Compose is a tool for defining and running multi-container applications. It is the key to unlocking a streamlined and efficient development and deployment experience.
Compose simplifies the control of your entire application stack, making it easy to manage services, networks, and volumes in a single, comprehensible YAML configuration file. Then, with a single command, you create and start all the services from your configuration file.

**commands handson
