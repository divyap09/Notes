<h2>Kubernetes (K8S)</h2>
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
<ol>
  <li>Master node (api server, controller manager, scheduler)</li>
  <li>Worker nodes</li>
</ol>


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
<ol>
  <li>Creation (API server -> etcd -> scheduler -> Kubelet -> Runtime -> update in etcd)</li>
  <li>Deletion (API server -> etcd (grace period) -> Kubelet -> Runtime controller)</li>
  <li>Pod state(tells where it is in the life cycle)</li>
  <li>Pending</li>
  <li>Running</li>
  <li>Succeeded</li>
  <li>Failed</li>
  <li>Unknown (communication issues)</li>
</ol>



Example:
```
kubectl run nginx --image=mynginx1
kubectl get pods
kubectl describe pod mynginx1
kubectl delete pod mynginx1-794574cd66-799zk

kubectl get pods -o wide (gives ip address and assigned node)
```

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

```
kubectl create deployment mynginx1 --image=nginx

kubectl create -f “myfilename.yaml”
```

Namespaces:
<ul>
	<li>Allows to group resources</li>
	<li>Deleting a namespace will delete all its child objects</li>
</ul>

```
kubectl get ns 
kubectl create/delete ns [namespace name]
```


 
Helm charts:
-	Provides a better way to manage all the Kubernetes YAML files we create on Kubernetes projects.



CI/CD techniques

 ```
sudo yum -y update

sudo yum -y install epel-release

sudo yum -y install libvirt qemu-kvm virt-install virt-top libguestfs-tools bridge-utils
```
 
Doubts:

How to know which YAML file is running, is it from docker or Kubernetes?

