# Container
- Containers are completely isolated environments, as in they can have their own processes or services, their own network interfaces, their own mounts, just like Virtual machines, except that they all share the same OS kernel.
- Containers have existed for about 10 years now and some of the different types of containers are LXC, LXD , LXCFS etc. Docker utilizes LXC containers.



![image](https://user-images.githubusercontent.com/29313557/114758286-6c17c480-9d7a-11eb-8b41-48a726052994.png)

![image](https://user-images.githubusercontent.com/29313557/114758488-a6816180-9d7a-11eb-9da8-2872b752504d.png)


**Containerization approach takes care of several issues:**
- No platform specific, IDE, or programming language restrictions.
- Small image sizes, making it easier to ship and store.
- No compatibility issues relating to the dependencies/versions/setup.
- Quick and easy application instance deployment.
- Applications and their resources are isolated, leading to better modularity and security.

 # Docker
 
![image](https://user-images.githubusercontent.com/29313557/114752888-70d97a00-9d74-11eb-9d82-5e36a28c6585.png)


![image](https://user-images.githubusercontent.com/29313557/114753026-a41c0900-9d74-11eb-8137-25aa521e9b65.png)


 ## Docker Architecture and Operations
 
![image](https://user-images.githubusercontent.com/29313557/114761644-67eda600-9d7e-11eb-94db-a1f724d6ccfd.png)


![image](https://user-images.githubusercontent.com/29313557/114759127-640c5480-9d7b-11eb-8b0c-b9375d04eafb.png)

 ### Images
 - An image is a package or a template, just like a VM template that you might have worked with in the virtualization world. It is used to create one or more containers.
 - Images are created with the docker build command, either by us or by other docker users.
 - Images are composed of layers of other images.
 - Images are stored in Docker registry.
 
 ### Containers
 - Containers are running instances off images that are isolated and have their own environments and set of processes.
 - If an image is a class, then a container is an instance of a class - a runtime object.
 - Containers are lightweight and portable encapsulations of an environment in which to run programs.
 - Containers are created from images. Inside a container, it has all the binaries and dependencies needed to run the application.


 ### Docker daemon 
 The daemon is responsible for all container related actions and receives commands via the CLI or the REST API.
 
 ### Docker Client
 A Docker client is how users interact with Docker. The Docker client can reside on the same host as the daemon or a remote  host.

 ### Registries and Repositories
 - A registry is where we store our images.
 - You can host your own registry, or you can use Docker public registry which is called DockerHub.
 - Inside a registry, images are stored repositories.
 - Docker repository is a collection of different docker images with the same name, that have different tags, each tag usually means a different version of the image.
 - DockerHub is a popular service for repositories.
 - Official names are reviewed by DockerHub.
 - If you don't specify a tag, it defaults to latest.
 - Docker will use the local image first if it's available, otherwise it will download it from the network.
 
 ## Docker Commands

![image](https://user-images.githubusercontent.com/29313557/114758891-1d1e5f00-9d7b-11eb-87aa-b13b4ee9fdae.png)

![image](https://user-images.githubusercontent.com/29313557/114759278-98801080-9d7b-11eb-8161-e4ceeae5f49d.png)

![image](https://user-images.githubusercontent.com/29313557/114759449-c9f8dc00-9d7b-11eb-841d-60f0c1f6c206.png)


![image](https://user-images.githubusercontent.com/29313557/114759529-e6951400-9d7b-11eb-8952-30bdbb80e315.png)

![image](https://user-images.githubusercontent.com/29313557/114759617-062c3c80-9d7c-11eb-92e4-e209352da0e7.png)

![image](https://user-images.githubusercontent.com/29313557/114759692-1fcd8400-9d7c-11eb-85ea-edbe6c4aadc8.png)

![image](https://user-images.githubusercontent.com/29313557/114759794-3d025280-9d7c-11eb-9a41-5b239d853c1f.png)

![image](https://user-images.githubusercontent.com/29313557/114759885-5905f400-9d7c-11eb-95bd-935f53e6f218.png)

![image](https://user-images.githubusercontent.com/29313557/114763983-0c70e780-9d81-11eb-9bc0-384dd7f3e3a6.png)

![image](https://user-images.githubusercontent.com/29313557/114764181-404c0d00-9d81-11eb-859e-864ff4fe2ee2.png)

we would like to execute a command on a running container. For example, when I run the **docker ps** command I can see that there is a running container. Let’s say I would
like to see the contents of a file inside the running container. I could use the **docker exec** command to execute a command on my docker container.

![image](https://user-images.githubusercontent.com/29313557/114764393-843f1200-9d81-11eb-812c-682b4244773f.png)

We learned that we could use the **docker run** Ubuntu command to run a container. In this case the latest version of Ubuntu. But what if we want to run another version of Ubuntu? Like for example the version 17.04. Then you specify the version separated by a colon. This is called a **tag**. Also, notice that if you don’t specify any tag as in the previous command, docker will consider the default tag which is “latest”

![image](https://user-images.githubusercontent.com/29313557/114764619-cd8f6180-9d81-11eb-97fa-c6775b175af4.png)

![image](https://user-images.githubusercontent.com/29313557/114764790-fb74a600-9d81-11eb-8251-83272fb5681e.png)

![image](https://user-images.githubusercontent.com/29313557/114764872-16471a80-9d82-11eb-9ba6-7539e2b5633e.png)

![image](https://user-images.githubusercontent.com/29313557/114764996-4098d800-9d82-11eb-85c1-9623e4381a26.png)


![image](https://user-images.githubusercontent.com/29313557/114765167-776eee00-9d82-11eb-8062-125221f51174.png)

![image](https://user-images.githubusercontent.com/29313557/114765339-ac7b4080-9d82-11eb-8e3b-b40cd8c0f5fa.png)

![image](https://user-images.githubusercontent.com/29313557/114765416-c61c8800-9d82-11eb-9fb0-8de44841671d.png)

![image](https://user-images.githubusercontent.com/29313557/114765496-d7659480-9d82-11eb-9a0a-6b2af363be86.png)

![image](https://user-images.githubusercontent.com/29313557/114765573-ee0beb80-9d82-11eb-83ed-ab0a6f9fb0c2.png)

All the layers built are cached by Docker. So, in case a particular step was to fail, for example in this case Step 3 failed and you were to fix the issue and re run docker
build, it will re use the previous layers from cache and continue to build the remaining layers. The same is true if you were to add additional steps in the Dockerfile . This way rebuilding your image is faster and you don’t have to wait for Docker to rebuilt the entire image each time. This is helpful especially when you update source code of your application as it may change more frequently. Only the layers above the updated layers needs to be rebuild.

### Docker Compose 

![image](https://user-images.githubusercontent.com/29313557/114765953-6c688d80-9d83-11eb-999f-a04d65fbf56d.png)

Earlier we saw how to deploy a stack using docker run command. You could use the docker run command if you wanted to deploy a test container of some kind. Instead of running separate docker run commands a better way to do this is to define your configuration in a docker compose file. A docker compose file is a file in YAML format were you define the different services involved in your application such as web, database, messaging, orchestration etc. Once the file is defined, running the **docker compose up** command will bring up the stack.

![image](https://user-images.githubusercontent.com/29313557/114766296-d7b25f80-9d83-11eb-8072-510a9ae9da92.png)

![image](https://user-images.githubusercontent.com/29313557/114766603-3aa3f680-9d84-11eb-8161-f8ee2924c711.png)

### Docker Networking

![image](https://user-images.githubusercontent.com/29313557/114766950-a7b78c00-9d84-11eb-96fa-98a404c7784d.png)

When you install Docker, it creates three networks automatically Bridge, Null and Host. Bridge is the default network a container gets attached to. If you would like to associate the container with any other network specify the network information using the network command line parameter like this.With the none network the containers are not attached to any network and doesn’t have any access to the external network or other containers.

![image](https://user-images.githubusercontent.com/29313557/114767163-eea58180-9d84-11eb-8d13-2a24b0aae161.png)

Run the **docker network ls** command to list all networks.

## How to create a Docker Image?
We have 2 ways to create a Docker Image:
 ### Interactive Method
 **Step 1) Pull the Base Image** : We first need an Image to run our docker container. We will use the latest Ubuntu docker image. To download or pull the image from DockerHub registry, docker pull can be used:
  
  ```$ docker pull Ubuntu```
  
  ![image](https://user-images.githubusercontent.com/29313557/113879334-0a82b380-97d8-11eb-97c2-f6a3ff3f80aa.png)
  
  **Step2) Deploy the Container** : We will run a Docker container using the Ubuntu image that we pulled in the previous step. We will use the run command. The -it options instruct the container to launch in interactive mode and enable a terminal typing interface.
  
  ```$ docker run -it --name <name of container> ubuntu```
  ![image](https://user-images.githubusercontent.com/29313557/113879531-3bfb7f00-97d8-11eb-86bc-a0d59e326cbc.png)

 **Step 3) Modify the Container** : Now we can do any changes we want. Here, we will be installing Nmap software in our container. As it is an Ubuntu image container, we will use apt-get command to install any software.
 
 ```$ apt-get install nmap```
 
 ![image](https://user-images.githubusercontent.com/29313557/113879637-59304d80-97d8-11eb-8445-4dcd4caf1539.png)

Once you finish modifying the new container, exit out of it.

```$ exit```

We will need the CONTAINER ID to save the changes we have made to the existing image. Run the docker ps -a to list all the containers and copy the Container ID.

```$ docker ps -a```

![image](https://user-images.githubusercontent.com/29313557/113879773-80871a80-97d8-11eb-9b56-4c7421869d8e.png)

**Step 4) Commit changes to Image**: Finally, we will create a new Image by committing the changes using the commit command.

```$ docker commit```

![image](https://user-images.githubusercontent.com/29313557/113879893-9ac0f880-97d8-11eb-8352-d123a10a9743.png)
  
### Dockerfile Method
 A Dockerfile is a document file that contains collections of commands that will be executed in the docker environment for building a new docker image. This file is written in  YAML Language. These images consist of read-only layers each of which represents a Dockerfile instruction. It is a more systematic, flexible and efficient way to build a Docker image.
![image](https://user-images.githubusercontent.com/29313557/113880002-b62c0380-97d8-11eb-83bc-549d9fca5fc2.png)
The following table shows the commonly used Dockerfile statements:
![image](https://user-images.githubusercontent.com/29313557/113878867-9ea04b00-97d7-11eb-9e48-a10ba78f9d09.png)

Example of a DockerFile
```
# Using the official Ubuntu as base
FROM ubuntu
RUN apt-get update
RUN apt-get install -y nginx
COPY index.nginx-debian.html /var/www/html
EXPOSE 80
COPY [“./start.sh”, ”/root/start.sh”]
ENTRYPOINT /root/start.sh
```
In this demo DockerFile,

- The first line “#using the official Ubuntu as a base” is a comment. You can add comments to the Docker File with the help of the # command
- The next line has to start with the **FROM** keyword. It tells docker, which base image is to be used. In our example, we are creating an image from the ubuntu image.
- The **RUN** command is used to run instructions against the image. In our case, we first update our Ubuntu system and then install the Nginx server on our ubuntu image.
- The **COPY** command is used to copy a file inside the /var/www/html folder.
- The next command is **EXPOSE**, which is used to expose the port number.
- The **ENTRYPOINT** command will run the /root/start.sh when the container starts.

To build an image from the dockerfile, we use the build command:
```
$ docker image build 

OR 

$ docker build
```
![image](https://user-images.githubusercontent.com/29313557/113880386-13c05000-97d9-11eb-94f1-607d29b6e34b.png)

Our image is successfully built and stored in the local repository. We can check it using the below commands:
```
$ docker images

 OR 

$ docker images ls
```
![image](https://user-images.githubusercontent.com/29313557/113880508-2e92c480-97d9-11eb-9c2d-f4a99258f745.png)


- 

## Best Practices for Building Images
The following best practices are recommended when you build images by writing Dockerfiles:

- **Containers should be ephemeral** in the sense that you can stop or delete a container at any moment and replace it with a new container from the Dockerfile with minimal set-up and configuration.  
- Use a **.dockerignore** file to reduce image size and reduce build time by excluding files from the build context that are unnecessary for the build. The build context is the full recursive contents of the directory where the Dockerfile was when the image was built.
- **Reduce image file sizes** (and attack surface) while keeping Dockerfiles readable by applying either a builder pattern or a multi-stage build  (available only in Docker 17.05 or higher).
- With a **builder pattern**, you maintain two Dockerfiles – one to build an application inside the image and a second Dockerfile that includes only the resulting application binaries from the first image to generate a second, streamlined image that is production ready. This pattern requires a custom script in order to automatically apply the transformation from the “development” image to the “production” image (for an example, see the Docker documentation: Before Multi-Stage Builds ).
- A **multi-stage build** allows you to use multiple FROM statements in a single Dockerfile and selectively copy artifacts from one stage to another, leaving behind everything you don’t want in the final image. You can, therefore, reduce image file sizes without the hassle of maintaining separate Dockerfiles and custom scripts when using the builder pattern.
- **Don’t install unnecessary packages** when building images.
- **Use multi-line commands instead of multiple RUN commands** for faster builds when possible (for example, when installing a list of packages).
- **Sort multi-line lists of packages into alphanumerical order** to easily identify duplicates and make it easier to update and review the list.
- **Enable content trust** when operating with a remote Docker registry so that you can only push, pull, run, or build trusted images which have been digitally signed to verify their integrity. When you use Docker with content trust, commands only operate on tagged images that have been digitally signed. Less trustworthy unsigned image tags are invisible when you enable content trust (off by default). To enable it, set the DOCKER_CONTENT_TRUST environment variable to 1. For further information see the Docker documentation:  Content trust in Docker.

## Docker Administration
- **Docker Configuration** — After installing Docker and starting Docker, the dockerd daemon runs with its default configuration. This page gathers resources on how to customize the configuration, Docker registry configuration, start the daemon manually, and troubleshoot and debug the daemon if run into issues.
- **Collecting Docker Metrics** — In order to get as much efficiency out of Docker as possible, we need to track Docker metrics. Monitoring metrics is also important for troubleshooting problems. This page gathers resources on how to collect Docker metrics with tools like Prometheus, Grafana, InfluxDB and more.
Starting and Restarting Docker Containers Automatically — Docker provides restart policies to control whether your containers start automatically when they exit, or when Docker restarts. Restart policies ensure that linked containers are started in the correct order. This page gathers resources about how to automatically start Docker container on boot or after server crash.
- **Managing Container Resources** — Resource management for Docker containers is a huge requirement for production users. It is necessary for running multiple containers on a single host in an efficient way and to ensure that one container does not starve the others in terms of cpu, memory, io, or networking. This page gathers resources about how to improve Docker performance by managing it’s resources.
- **Controlling Docker With systemd** — Systemd provides a standard process for controlling programs and processes on Linux hosts. One of the nice things about systemd is that it is a single command that can be used to manage almost all aspects of a process. This page gathers resources about how to use systemd with Docker daemon service.
- **Docker CLI Commands** — There are a large number of Docker client CLI commands, which provide information relating to various Docker objects on a given Docker host or Docker Swarm cluster. Generally, this output is provided in a tabular format. This page gathers resources about how the Docker CLI Work, CLI Tips and Tricks and basic Docker CLI commands.
- **Docker Logging** — Logs tell the full story of what is happening, or what happened at every layer of the stack. Whether it’s the application layer, the networking layer, the infrastructure layer, or storage, logs have all the answers. This page gathers resources about working with Docker logs, how to manage and implement Docker logs and more.
Troubleshooting Docker Engine — Docker makes everything easier. But even with the easiest platforms, sometimes you run into problems. This page gathers resources about  how to diagnose and troubleshoot problems, send logs, and communicate with the Docker Engine.
- **Docker Orchestration – Tools and Options** — To get the full benefit of Docker container, you need software to move containers around in response to auto-scaling events, a failure of the backing host, and deployment updates. This is container orchestration. This page gathers resources about Docker orchestration tools, fundamentals and best practices.

![image](https://user-images.githubusercontent.com/29313557/114074426-fb783000-98c1-11eb-98c9-6994b3adccd9.png)

## How Do They Differ from Docker?
Let us take a quick look at how each of these alternatives differs from Docker:

![image](https://user-images.githubusercontent.com/29313557/114076981-ebae1b00-98c4-11eb-98ae-9ff57aca4c86.png)

# Container Orchestration 
Container orchestration is a process that automates the deployment, management, scaling, networking, and availability of container-based applications.
- Provisioning hosts
- Instantiating a set of containers
- Rescheduling failed containers
- Linking containers together through agreed interfaces
- Exposing services to machines outside of the cluster
- Scaling out or down the cluster by adding or removing containers

## Where does container orchestration fit within the system stack?
![image](https://user-images.githubusercontent.com/29313557/113820731-b99f9a80-9798-11eb-98f4-faae1eaccf37.png)

Three main functional aspects of what they do include:
- **Service Management:** Labels, groups, namespaces, dependencies, load balancing, readiness checks.
- **Scheduling:** Allocation, replication, resurrection, rescheduling, rolling deployment, upgrades, downgrades.
- **Resource Management:** Memory, CPU, GPU, volumes, ports, IPs.

Non-functional aspects that are important: scalability, availability, flexibility, usability, portability, and security.

## What are some Container Orchestration tools available?

![image](https://user-images.githubusercontent.com/29313557/113820866-e8b60c00-9798-11eb-8e72-3f909e0b79bc.png)

- **Docker Swarm:** Provides native clustering functionality for Docker containers, which turns a group of Docker engines into a single, virtual Docker engine.
 
 ![image](https://user-images.githubusercontent.com/29313557/114766427-029cb380-9d84-11eb-8822-9f7b1526a64a.png)
 
 ![image](https://user-images.githubusercontent.com/29313557/114766533-2233dc00-9d84-11eb-9b89-8c91a2d8dbd1.png)




- **Google Container Engine:** Google Container Engine, built on Kubernetes, lets you run Docker containers on the Google Cloud.
- **Kubernetes:** An orchestration system for Docker containers. It handles scheduling and manages workloads based on user-defined parameters.
- **Mesosphere Marathon:** Marathon is a container orchestration framework for Apache Mesos that is designed to launch long-running applications.
- **Amazon ECS:** The ECS supports Docker containers and lets you run applications on a managed cluster of Amazon EC2 instances.
- **Azure Container Service (ACS):** ACS lets you create a cluster of virtual machines that act as container hosts along with master machines that are used to manage your application containers.
- **Cloud Foundry’s Diego:** Container management system that combines a scheduler, runner, and health manager.
- **CoreOS Fleet:** Container management tool that lets you deploy Docker containers on hosts in a cluster as well as distribute services across a cluster.

  
  ## Kubernetes
  
  https://github.com/kodekloudhub/certified-kubernetes-administrator-course
  
  ### Cluster Architecture
  - 10,000 Feet Look at the Kubernetes Architecture

  ![image](https://user-images.githubusercontent.com/29313557/114768964-2d3c3b80-9d87-11eb-8400-e5f7a5669720.png)
  
  ![image](https://user-images.githubusercontent.com/29313557/114768992-35947680-9d87-11eb-95f9-58577b5342c7.png)
  
  #### What is a ETCD?
     - ETCD is a distributed reliable key-value store that is simple, secure & Fast.
     
  #### What is a Key-Value Store
   - Traditionally, databases have been in tabular format, you must have heared about SQL or Relational databases. They store data in rows and columns
       
     !![image](https://user-images.githubusercontent.com/29313557/114769135-6c6a8c80-9d87-11eb-903a-b610019a9e5b.png)
     
   - A Key-Value Store stores information in a Key and Value format.
       
     ![image](https://user-images.githubusercontent.com/29313557/114769150-712f4080-9d87-11eb-92af-b06a165ea3aa.png)
     
  #### Run the ETCD Service
       ```
       $ ./etcd
       ```
     - When you start **`ETCD`** it will by default listens on port **`2379`**
      - The default client that comes with **`ETCD`** is the **`etcdct`** client. You can use it to store and retrieve key-value pairs.
        ```
        Syntax: To Store a Key-Value pair
        $ ./etcdctl set key1 value1
        ```
        ```
        Syntax: To retrieve the stored data
        $ ./etcdctl get key1
        ```
        ```
        Syntax: To view more commands. Run etcdctl without any arguments
        $ ./etcdctl
        ```
        
        ![image](https://user-images.githubusercontent.com/29313557/114769358-bb182680-9d87-11eb-885c-b95a78ba2f46.png)

 ### ETCD in Kubernetes
 
 #### ETCD Datastore
  - The ETCD Datastore stores information regarding the cluster such as **`Nodes`**, **`PODS`**, **`Configs`**, **`Secrets`**, **`Accounts`**, **`Roles`**, **`Bindings`** and   **`Others`**.
 - Every information you see when you run the **`kubectl get`** command is from the **`ETCD Server`**.

#### Setup - Manual
- If you setup your cluster from scratch then you deploy **`ETCD`** by downloading ETCD Binaries yourself
- Installing Binaries and Configuring ETCD as a service in your master node yourself.
  ```
  $ wget -q --https-only "https://github.com/etcd-io/etcd/releases/download/v3.3.11/etcd-v3.3.11-linux-amd64.tar.gz"
  ```

  ![image](https://user-images.githubusercontent.com/29313557/114769644-1a763680-9d88-11eb-9f28-dae0524dc4c0.png)
  
#### Setup - Kubeadm
- If you setup your cluster using **`kubeadm`** then kubeadm will deploy etcd server for you as a pod in **`kube-system`** namespace.
  ```
  $ kubectl get pods -n kube-system
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114769698-2bbf4300-9d88-11eb-8c5f-0fd215d6469b.png)

#### Explore ETCD
- To list all keys stored by kubernetes, run the below command
  ```
  $ kubectl exec etcd-master -n kube-system etcdctl get / --prefix -key
  ```
- Kubernetes Stores data in a specific directory structure, the root directory is the **`registry`** and under that you have varies kubernetes constructs such as **`minions`**, **`nodes`**, **`pods`**, **`replicasets`**, **`deployments`**, **`roles`**, **`secrets`** and **`Others`**.
  
  ![image](https://user-images.githubusercontent.com/29313557/114769742-38439b80-9d88-11eb-9e9c-890ae6473c65.png)

 #### ETCD in HA Environment
   - In a high availability environment, you will have multiple master nodes in your cluster that will have multiple ETCD Instances spread across the master nodes.
   - Make sure etcd instances know each other by setting the right parameter in the **`etcd.service`** configuration. The **`--initial-cluster`** option where you need to  specify the different instances of the etcd service.
     ![image](https://user-images.githubusercontent.com/29313557/114769774-41346d00-9d88-11eb-9c29-24b769ec0018.png)


### Kube API Server
  
#### Kube-apiserver is the primary component in kubernetes.
- Kube-apiserver is responsible for **`authenticating`**, **`validating`** requests, **`retrieving`** and **`Updating`** data in ETCD key-value store. In fact kube-apiserver is the only component that interacts directly to the etcd datastore. The other components such as kube-scheduler, kube-controller-manager and kubelet uses the API-Server to update in the cluster in their respective areas.
  
  ![image](https://user-images.githubusercontent.com/29313557/114770530-2ca4a480-9d89-11eb-8537-4ec160adac19.png)
  
#### Installing kube-apiserver

- If you are bootstrapping kube-apiserver using **`kubeadm`** tool, then you don't need to know this, but if you are setting up using the hardway then kube-apiserver is available as a binary in the kubernetes release page.
  - For example: You can downlaod the kube-apiserver v1.13.0 binary here [kube-apiserver](https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-apiserver)
    ```
    $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-apiserver
    ```
 
![image](https://user-images.githubusercontent.com/29313557/114770897-991fa380-9d89-11eb-9210-51034013db3b.png)
 
#### View kube-apiserver - Kubeadm
- kubeadm deploys the kube-apiserver as a pod in kube-system namespace on the master node.
  ```
  $ kubectl get pods -n kube-system
  ```
   
  ![image](https://user-images.githubusercontent.com/29313557/114770938-a341a200-9d89-11eb-8ae9-477c4a24c19f.png)
   
#### View kube-apiserver options - Kubeadm
- You can see the options with in the pod definition file located at **`/etc/kubernetes/manifests/kube-apiserver.yaml`**
  ```
  $ cat /etc/kubernetes/manifests/kube-apiserver.yaml
  ```
  
  ![image](https://user-images.githubusercontent.com/29313557/114770967-ab014680-9d89-11eb-93a0-4ceb20d08d8e.png)
   
#### View kube-apiserver options - Manual
- In a Non-kubeadm setup, you can inspect the options by viewing the kube-apiserver.service
  ```
  $ cat /etc/systemd/system/kube-apiserver.service
  ```
  
  ![image](https://user-images.githubusercontent.com/29313557/114771003-b5234500-9d89-11eb-8ef9-9c6eacf0bd2e.png)
   
- You can also see the running process and affective options by listing the process on master node and searching for kube-apiserver.
  ```
  $ ps -aux |grep kube-apiserver
  ```
 ![image](https://user-images.githubusercontent.com/29313557/114771013-b9e7f900-9d89-11eb-8c57-8676a9c0c085.png)

## Kube Controller Manager

#### Kube Controller Manager manages various controllers in kubernetes.
- In kubernetes terms, a controller is a process that continously monitors the state of the components within the system and works towards bringing the whole system to the desired functioning state.

#### Node Controller
   - Responsible for monitoring the state of the Nodes and taking necessary actions to keep the application running. 
  
   ![image](https://user-images.githubusercontent.com/29313557/114777163-fb2fd700-9d90-11eb-9ec0-72d1c3104242.png)
   
#### Replication Controller
   - It is responsible for monitoring the status of replicasets and ensuring that the desired number of pods are available at all time within the set.
   
   ![image](https://user-images.githubusercontent.com/29313557/114777176-0256e500-9d91-11eb-8e42-7120e7fbbeae.png)
   
#### Other Controllers
   - There are many more such controllers available within kubernetes
     
   ![image](https://user-images.githubusercontent.com/29313557/114777192-07b42f80-9d91-11eb-9b57-dc6b5793796c.png)
   
   
  #### Installing Kube-Controller-Manager
  - When you install kube-controller-manager the different controllers will get installed as well.
  - Download the kube-controller-manager binary from the kubernetes release page. For example: You can download kube-controller-manager v1.13.0 here [kube-controller-manager](https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-controller-manager)
    ```
    $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-controller-manager
    ```
  - By default all controllers are enabled, but you can choose to enable specific one from **`kube-controller-manager.service`**
    ```
    $ cat /etc/systemd/system/kube-controller-manager.service
    ```
    ![image](https://user-images.githubusercontent.com/29313557/114777220-139ff180-9d91-11eb-90ad-4090a488b8b3.png)
    
#### View kube-controller-manager - kubeadm
- kubeadm deploys the kube-controller-manager as a pod in kube-system namespace
  ```
  $ kubectl get pods -n kube-system
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114777245-1c90c300-9d91-11eb-84c5-3f0b70d72a8b.png)
  
#### View kube-controller-manager options - kubeadm
- You can see the options within the pod located at **`/etc/kubernetes/manifests/kube-controller-manager.yaml`**
  ```
  $ cat /etc/kubernetes/manifests/kube-controller-manager.yaml
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114777273-231f3a80-9d91-11eb-8d1c-f93ae2fadfa2.png)
  
#### View kube-controller-manager options - Manual
- In a non-kubeadm setup, you can inspect the options by viewing the **`kube-controller-manager.service`**
  ```
  $ cat /etc/systemd/system/kube-controller-manager.service
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114777289-287c8500-9d91-11eb-9fa3-eafc5506fc9e.png)
  
- You can also see the running process and affective options by listing the process on master node and searching for kube-controller-manager.
  ```
  $ ps -aux |grep kube-controller-manager
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114777310-2e726600-9d91-11eb-809f-ad5a72df925d.png)
 
### Kube Scheduler
#### kube-scheduler is responsible for scheduling pods on nodes.  
- The kube-scheduler is only responsible for deciding which pod goes on which node. It doesn't actually place the pod on the nodes, thats the job of the **`kubelet`**.

  ![image](https://user-images.githubusercontent.com/29313557/114788331-e5291300-9d9e-11eb-851d-cd866794220b.png)
  
#### Why do you need a Scheduler?

  ![image](https://user-images.githubusercontent.com/29313557/114788346-ebb78a80-9d9e-11eb-8407-e721df3c4401.png)
    
#### Install kube-scheduler - Manual
- Download the kubescheduler binary from the kubernetes release pages [kube-scheduler](https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-scheduler). For example: To download kube-scheduler v1.13.0, Run the below command.
  ```
  $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-scheduler
  ```
- Extract it
- Run it as a service

  ![image](https://user-images.githubusercontent.com/29313557/114788379-f83be300-9d9e-11eb-8d67-b7c7ebeae6f2.png)
  
#### View kube-scheduler options - kubeadm
- If you set it up with kubeadm tool, kubeadm tool will deploy the kube-scheduler as pod in kube-system namespace on master node.
  ```
  $ kubectl get pods -n kube-system
  ```
- You can see the options for kube-scheduler in pod definition file that is located at **`/etc/kubernetes/manifests/kube-scheduler.yaml`**
  ```
  $ cat /etc/kubernetes/manifests/kube-scheduler.yaml
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114788392-fd992d80-9d9e-11eb-833e-7e8f64f7ed3c.png)
  
- You can also see the running process and affective options by listing the process on master node and searching for kube-apiserver.
  ``` 
  $ ps -aux |grep kube-scheduler
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114788412-0558d200-9d9f-11eb-80c9-53950587eec0.png)
  
### Kubelet
#### Kubelet is the sole point of contact for the kubernetes cluster
- The **`kubelet`** will create the pods on the nodes, the scheduler only decides which pods goes where.

  ![image](https://user-images.githubusercontent.com/29313557/114788572-549f0280-9d9f-11eb-86e6-5f3a25188a8d.png)
  
#### Install kubelet
- Kubeadm does not deploy kubelet by default. You must manually download and install it.
- Download the kubelet binary from the kubernetes release pages [kubelet](https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kubelet). For example: To download kubelet v1.13.0, Run the below command.
  ```
  $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kubelet
  ```
- Extract it
- Run it as a service

  ![image](https://user-images.githubusercontent.com/29313557/114788597-5d8fd400-9d9f-11eb-95de-219fd439c21e.png)
  
#### View kubelet options
- You can also see the running process and affective options by listing the process on worker node and searching for kubelet.
  ``` 
  $ ps -aux |grep kubelet
  ```
  
  ![image](https://user-images.githubusercontent.com/29313557/114788609-6385b500-9d9f-11eb-82ec-2d6f13ed87ca.png)
  
### Kube Proxy
Within Kubernetes Cluster, every pod can reach every other pod, this is accomplish by deploying a pod networking cluster to the cluster. 
- Kube-Proxy is a process that runs on each node in the kubernetes cluster.
  
  ![image](https://user-images.githubusercontent.com/29313557/114788676-8a43eb80-9d9f-11eb-8b47-d88a133d069a.png)
  
#### Install kube-proxy - Manual
- Download the kube-proxy binary from the kubernetes release pages [kube-proxy](https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-proxy). For example: To download kube-proxy v1.13.0, Run the below command.
  ```
  $ wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-proxy
  ```
- Extract it
- Run it as a service

  ![image](https://user-images.githubusercontent.com/29313557/114788695-9039cc80-9d9f-11eb-90e4-04e03336eeeb.png)

#### View kube-proxy options - kubeadm
- If you set it up with kubeadm tool, kubeadm tool will deploy the kube-proxy as pod in kube-system namespace. In fact it is deployed as a daemonset on master node.
  ```
  $ kubectl get pods -n kube-system
  ```
 ![image](https://user-images.githubusercontent.com/29313557/114788708-95971700-9d9f-11eb-841d-0fbe345090f6.png)
  

### Pods
- POD introduction
- How to deploy pod?

#### Kubernetes doesn't deploy containers directly on the worker node.

  ![image](https://user-images.githubusercontent.com/29313557/114788844-d131e100-9d9f-11eb-8be1-ceb71ded34c4.png)
  
#### Here is a single node kubernetes cluster with single instance of your application running in a single docker container encapsulated in the pod.

![image](https://user-images.githubusercontent.com/29313557/114788869-db53df80-9d9f-11eb-88b5-2866fec92b55.png)

#### Pod will have a one-to-one relationship with containers running your application.

  ![image](https://user-images.githubusercontent.com/29313557/114788894-e575de00-9d9f-11eb-9fd4-fcd949fe04d1.png)
  
#### Multi-Container PODs
- A single pod can have multiple containers except for the fact that they are usually not multiple containers of the **`same kind`**.
  
  ![image](https://user-images.githubusercontent.com/29313557/114788923-eeff4600-9d9f-11eb-9196-e9d92b29dd99.png)
  
#### Docker Example (Docker Link)
  
  ![image](https://user-images.githubusercontent.com/29313557/114788945-f7578100-9d9f-11eb-8d92-64d2ef291993.png)
  
#### How to deploy pods?
Lets now take a look to create a nginx pod using **`kubectl`**.

- To deploy a docker container by creating a POD.
  ```
  $ kubectl run nginx --image nginx
  ```

- To get the list of pods
  ```
  $ kubectl get pods
  ```

 ![image](https://user-images.githubusercontent.com/29313557/114788963-fe7e8f00-9d9f-11eb-8d14-6596fbbbd303.png)

### ReplicaSets
- Replication Controller
- ReplicaSet

#### Controllers are brain behind kubernetes

#### What is a Replica and Why do we need a replication controller?

  ![image](https://user-images.githubusercontent.com/29313557/114789332-941a1e80-9da0-11eb-9e25-48b9a94b9d8b.png)
  
  ![image](https://user-images.githubusercontent.com/29313557/114789339-99776900-9da0-11eb-8595-86ffa435cd27.png)
  
#### Difference between ReplicaSet and Replication Controller
- **`Replication Controller`** is the older technology that is being replaced by a **`ReplicaSet`**.
- **`ReplicaSet`** is the new way to setup replication.

#### Creating a Replication Controller

#### Replication Controller Definition File
  
   ![image](https://user-images.githubusercontent.com/29313557/114789356-a1370d80-9da0-11eb-9b61-50f7a4ba9ee4.png)
  
```
    apiVersion: v1
    kind: ReplicationController
    metadata:
      name: myapp-rc
      labels:
        app: myapp
        type: front-end
    spec:
     template:
        metadata:
          name: myapp-pod
          labels:
            app: myapp
            type: front-end
        spec:
         containers:
         - name: nginx-container
           image: nginx
     replicas: 3
```
  - To Create the replication controller
    ```
    $ kubectl create -f rc-definition.yaml
    ```
  - To list all the replication controllers
    ```
    $ kubectl get replicationcontroller
    ```
  - To list pods that are launch by the replication controller
    ```
    $ kubectl get pods
    ```
   ![image](https://user-images.githubusercontent.com/29313557/114789372-aac07580-9da0-11eb-9417-ca9662faca2a.png)
    
#### Creating a ReplicaSet
  
#### ReplicaSet Definition File

   ![image](https://user-images.githubusercontent.com/29313557/114789392-b1e78380-9da0-11eb-8360-ba6dffe325f4.png)

```
    apiVersion: apps/v1
    kind: ReplicaSet
    metadata:
      name: myapp-replicaset
      labels:
        app: myapp
        type: front-end
    spec:
     template:
        metadata:
          name: myapp-pod
          labels:
            app: myapp
            type: front-end
        spec:
         containers:
         - name: nginx-container
           image: nginx
     replicas: 3
     selector:
       matchLabels:
        type: front-end
 ```
#### ReplicaSet requires a selector definition when compare to Replicaton Controller.
   
  - To Create the replicaset
    ```
    $ kubectl create -f replicaset-definition.yaml
    ```
  - To list all the replicaset
    ```
    $ kubectl get replicaset
    ```
  - To list pods that are launch by the replicaset
    ```
    $ kubectl get pods
    ```
   
   ![image](https://user-images.githubusercontent.com/29313557/114789427-bca21880-9da0-11eb-9063-e3c01a9b3c8d.png)
    
##### Labels and Selectors
#### What is the deal with Labels and Selectors? Why do we label pods and objects in kubernetes?

  ![image](https://user-images.githubusercontent.com/29313557/114789445-c461bd00-9da0-11eb-8810-57d96f84e3cb.png)
  
#### How to scale replicaset
- There are multiple ways to scale replicaset
  - First way is to update the number of replicas in the replicaset-definition.yaml definition file. E.g replicas: 6 and then run 
 ```
    apiVersion: apps/v1
    kind: ReplicaSet
    metadata:
      name: myapp-replicaset
      labels:
        app: myapp
        type: front-end
    spec:
     template:
        metadata:
          name: myapp-pod
          labels:
            app: myapp
            type: front-end
        spec:
         containers:
         - name: nginx-container
           image: nginx
     replicas: 6
     selector:
       matchLabels:
        type: front-end
```

  ```
  $ kubectl apply -f replicaset-definition.yaml
  ```
  - Second way is to use **`kubectl scale`** command.
  ```
  $ kubectl scale --replicas=6 -f replicaset-definition.yaml
  ```
  - Third way is to use **`kubectl scale`** command with type and name
  ```
  $ kubectl scale --replicas=6 replicaset myapp-replicaset
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114789572-f3782e80-9da0-11eb-9ec0-e263cc0236ec.png)

### Deployments

#### Deployment is a kubernetes object. 
  
 ![image](https://user-images.githubusercontent.com/29313557/114789692-228ea000-9da1-11eb-9d4d-45daa5be1d57.png)
  
#### How do we create deployment?

```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: myapp-deployment
      labels:
        app: myapp
        type: front-end
    spec:
     template:
        metadata:
          name: myapp-pod
          labels:
            app: myapp
            type: front-end
        spec:
         containers:
         - name: nginx-container
           image: nginx
     replicas: 3
     selector:
       matchLabels:
        type: front-end
 ```
- Once the file is ready, create the deployment using deployment definition file
  ```
  $ kubectl create -f deployment-definition.yaml
  ```
- To see the created deployment
  ```
  $ kubectl get deployment
  ```
- The deployment automatically creates a **`ReplicaSet`**. To see the replicasets
  ```
  $ kubectl get replicaset
  ```
- The replicasets ultimately creates **`PODs`**. To see the PODs
  ```
  $ kubectl get pods
  ```
    
 ![image](https://user-images.githubusercontent.com/29313557/114789712-2a4e4480-9da1-11eb-9989-6c4d4e6080e8.png)
  
- To see the all objects at once
  ```
  $ kubectl get all
  ```
 ![image](https://user-images.githubusercontent.com/29313557/114789731-2f12f880-9da1-11eb-8caf-0775556d02fd.png)
 
 
 ### Namespaces
So far in this course we have created **`Objects`** such as **`PODs`**, **`Deployments`** and **`Services`** in our cluster. Whatever we have been doing we have been doing in a **`NAMESPACE`**.
- This namespace is the **`default`** namespace in kubernetes. It is automatically created when kubernetes is setup initially.

  ![image](https://user-images.githubusercontent.com/29313557/114789931-7dc09280-9da1-11eb-950c-f6bf74eb2f68.png)
 
- You can create your own namespaces as well.

  ![image](https://user-images.githubusercontent.com/29313557/114789945-844f0a00-9da1-11eb-9ee5-6174649c18a7.png)
  
- To list the pods in default namespace
  ```
  $ kubectl get pods
  ```
- To list the pods in another namespace. Use **`kubectl get pods`** command along with the **`--namespace`** flag or argument.
  ```
  $ kubectl get pods --namespace=kube-system
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114789961-8a44eb00-9da1-11eb-8f1f-a1f7141deb31.png)
  
- Here we have a pod definition file, when we create a pod with pod-definition file, the pod is created in the default namespace.

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
     app: myapp
     type: front-end
spec:
  containers:
  - name: nginx-container
    image: nginx
 ```
  ```
  $ kubectl create -f pod-definition.yaml
  ```
- To create the pod with the pod-definition file in another namespace, use the **`--namespace`** option.
  ```
  $ kubectl create -f pod-definition.yaml --namespace=dev
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114789976-92048f80-9da1-11eb-9da2-cc9fd91a6396.png)

- If you want to make sure that this pod gets you created in the **`dev`** env all the time, even if you don't specify in the command line, you can move the **`--namespace`** definition into the pod-definition file.
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  namespace: dev
  labels:
     app: myapp
     type: front-end
spec:
  containers:
  - name: nginx-container
    image: nginx
 ```
  
  ![image](https://user-images.githubusercontent.com/29313557/114790008-9c268e00-9da1-11eb-9baf-f6641fe01837.png)
  
- To create a new namespace, create a namespace definition as shown below and then run **`kubectl create`**
```
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```

  ```
  $ kubectl create -f namespace-dev.yaml
  ```
  Another way to create a namespace
  ```
  $ kubectl create namespace dev
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114790019-a21c6f00-9da1-11eb-8bbf-5f6baea39a16.png)
  
- By default, we will be in a **`default`** namespace. To switch to a particular namespace permenently run the below command.
  ```
  $ kubectl config set-context $(kubectl config current-context) --namespace=dev
  ```
- To view pods in all namespaces
  ```
  $ kubectl get pods --all-namespaces
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114790038-a8aae680-9da1-11eb-8b61-db2c00f3cb14.png)
  
- To limit resources in a namespace, create a resource quota. To create one start with **`ResourceQuota`** definition file.
```
apiVersion: v1
kind: ResourceQuota
metadata:
  name: compute-quota
  namespace: dev
spec:
  hard:
    pods: "10"
    requests.cpu: "4"
    requests.memory: 5Gi
    limits.cpu: "10"
    limits.memory: 10Gi
```
  ```
  $ kubectl create -f compute-quota.yaml
  ```
  ![image](https://user-images.githubusercontent.com/29313557/114790054-ae083100-9da1-11eb-9729-73ed2a11e74e.png)
  
## Kubernetes Services
#### Services
- Kubernetes Services enables communication between various components within and outside of the application.

  ![image](https://user-images.githubusercontent.com/29313557/114791383-1821d580-9da4-11eb-9034-8b3971077216.png)
  
#### Let's look at some other aspects of networking

## External Communication

- How do we as an **`external user`** access the **`web page`**?

  - From the node (Able to reach the application as expected)
  
    ![image](https://user-images.githubusercontent.com/29313557/114791402-207a1080-9da4-11eb-9eab-8a77addde19a.png)
    
  - From outside world (This should be our expectation, without something in the middle it will not reach the application)
  
    ![image](https://user-images.githubusercontent.com/29313557/114791421-2d96ff80-9da4-11eb-8ce6-4366391fb8ef.png)
   
    
 ## Service Types
 
 #### There are 3 types of service types in kubernetes
 
   ![image](https://user-images.githubusercontent.com/29313557/114791439-34be0d80-9da4-11eb-9423-2413567d13fa.png)
 
 1. NodePort
    - Where the service makes an internal POD accessible on a POD on the NODE.
      ```
      apiVersion: v1
      kind: Service
      metadata:
       name: myapp-service
      spec:
       types: NodePort
       ports:
       - targetPort: 80
         port: 80
         nodePort: 30008
      ```
     ![image](https://user-images.githubusercontent.com/29313557/114791471-3daedf00-9da4-11eb-8b0d-24b56751cd2d.png)
      
      #### To connect the service to the pod
      ```
      apiVersion: v1
      kind: Service
      metadata:
       name: myapp-service
      spec:
       types: NodePort
       ports:
       - targetPort: 80
         port: 80
         nodePort: 30008
       selector:
         app: myapp
         type: front-end
       ```

    ![image](https://user-images.githubusercontent.com/29313557/114791491-46071a00-9da4-11eb-8fe3-fbcd822a5ced.png)
      
      #### To create the service
      ```
      $ kubectl create -f service-definition.yaml
      ```
      
      #### To list the services
      ```
      $ kubectl get services
      ```
      
      #### To access the application from CLI instead of web browser
      ```
      $ curl http://192.168.1.2:30008
      ```
      
      ![image](https://user-images.githubusercontent.com/29313557/114791591-646d1580-9da4-11eb-91a9-e938fd4fa388.png)

      #### A service with multiple pods
      
      ![image](https://user-images.githubusercontent.com/29313557/114791616-6c2cba00-9da4-11eb-8637-4b699597c641.png)
      
      #### When Pods are distributed across multiple nodes
     
      ![image](https://user-images.githubusercontent.com/29313557/114791638-72bb3180-9da4-11eb-9569-ee5311ae8a9f.png)
     
            
 1. ClusterIP
    - In this case the service creates a **`Virtual IP`** inside the cluster to enable communication between different services such as a set of frontend servers to a set of backend servers.
    
 1. LoadBalancer
    - Where the service provisions a **`loadbalancer`** for our application in supported cloud providers.

### Kubernetes Services - ClusterIP
#### ClusterIP
- In this case the service creates a **`Virtual IP`** inside the cluster to enable communication between different services such as a set of frontend servers to a set of backend servers.
    
   ![image](https://user-images.githubusercontent.com/29313557/114791794-b6ae3680-9da4-11eb-977a-92ebb6ccef0a.png)
    
#### What is a right way to establish connectivity between these services or tiers  
- A kubernetes service can help us group the pods together and provide a single interface to access the pod in a group.

  ![image](https://user-images.githubusercontent.com/29313557/114791803-bca41780-9da4-11eb-9e09-2d28b0000134.png)
  
#### To create a service of type ClusterIP
```
apiVersion: v1
kind: Service
metadata:
 name: back-end
spec:
 types: ClusterIP
 ports:
 - targetPort: 80
   port: 80
 selector:
   app: myapp
   type: back-end
```
```
$ kubectl create -f service-definition.yaml
```

#### To list the services
```
$ kubectl get services
```
 ![image](https://user-images.githubusercontent.com/29313557/114791816-c463bc00-9da4-11eb-8d83-288a567cdd72.png)
  
  

  

  



