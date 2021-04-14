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
  

