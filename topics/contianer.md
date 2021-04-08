# Container
Containerization is a technique that allows software to run reliably regardless of the computing environment. By encapsulating software within isolated environments called containers.
![image](https://user-images.githubusercontent.com/29313557/113821833-426b0600-979a-11eb-8775-ed43f8ce2116.png)

**Containerization approach takes care of several issues:**
- No platform specific, IDE, or programming language restrictions.
- Small image sizes, making it easier to ship and store.
- No compatibility issues relating to the dependencies/versions/setup.
- Quick and easy application instance deployment.
- Applications and their resources are isolated, leading to better modularity and security.

 ## Docker Architecture and Operations
![image](https://user-images.githubusercontent.com/29313557/113823042-cec9f880-979b-11eb-91f0-7d2aaab8b422.png)

 ### Docker daemon 
 The daemon is responsible for all container related actions and receives commands via the CLI or the REST API.
 ### Docker Client
 A Docker client is how users interact with Docker. The Docker client can reside on the same host as the daemon or a remote  host.

 ### Images
 - Images are read as templates used to create containers.
 - Images are created with the docker build command, either by us or by other docker users.
 - Images are composed of layers of other images.
 - Images are stored in Docker registry.
 
 ### Containers
 - If an image is a class, then a container is an instance of a class - a runtime object.
 - Containers are lightweight and portable encapsulations of an environment in which to run programs.
 - Containers are created from images. Inside a container, it has all the binaries and dependencies needed to run the application.

 ### Registries and Repositories
 - A registry is where we store our images.
 - You can host your own registry, or you can use Docker public registry which is called DockerHub.
 - Inside a registry, images are stored repositories.
 - Docker repository is a collection of different docker images with the same name, that have different tags, each tag usually means a different version of the image.
 - DockerHub is a popular service for repositories.
 - Official names are reviewed by DockerHub.
 - If you don't specify a tag, it defaults to latest.
 - Docker will use the local image first if it's available, otherwise it will download it from the network.

## Basic Docker Operations
- **Docker Image Repositories** — A Docker Image repository is a place where Docker Images are actually stored, compared to the image registry which is a collection of pointers to this images. This page gathers resources about public repositories like the Docker hub and private repositories and how to set up and manage Docker repositories.
- **Working With Dockerfiles** — The Dockerfile is essentially the build instructions to build the Docker image. The advantage of a Dockerfile over just storing the binary image is that the automatic builds will ensure you have the latest version available. This page gathers resources about working with Dockerfiles including best practices, Dockerfile commands, how to create Docker images with a Dockerfile and more.
- **Running Docker Containers** — All docker containers run one main process. After that process is complete the container stops running. This page gathers resources about how to run docker containers on different operating systems, including useful docker commands.
- **Working With Docker Hub** — Docker Hub is a cloud-based repository in which Docker users and partners create, test, store and distribute container images. Through Docker Hub, a user can access public, open source image repositories, as well as use a space to create their own private repositories, automated build functions, and work groups. This page gathers resources about Docker Hub and how to push and pull container images to and from Docker Hub.
- **Docker Container Management** — The true power of Docker container technology lies in its ability to perform complex tasks with minimal resources. If not managed properly they will bloat, bogging down the environment and reducing the capabilities they were designed to deliver. This page gathers resources about how to effectively manage Docker, how to pick the right management tool including a list of recomended tools.
- **Storing Data Within Containers** — It is possible to store data within the writable layer of a container. Docker offers three different ways to mount data into a container from the Docker host: volumes, bind mounts, or tmpfs volumes. This page gathers resources about various to store data with containers, the downsides like the persistent storage and information on how to manage data in Docker.
- **Docker Compliance** — While Docker Containers have fundamentally accelerated application development, organizations using them still must adhere to the same set of external regulations, including NIST, PCI and HIPAA.  They also must meet their internal policies for best practices and configurations. This page gathers resources about Docker compliance, policies, and its challenges.

## Common Operations
Some common operations you’ll need with Docker images include:

- **Build a new image from a Dockerfile:** The command for building an image from a Dockerfile is **docker build** , where you specify the location of the Dockerfile (it could be the current directory). You can (optionally) apply one or more tags to the resulting image using parameters. Use the **-t** option.
- List all local images: Use the **docker images** command to list all local images. The output includes image ID, repository, tags, and creation date.
- **Tagging an existing image:** You assign tags to images for clarification, so users know the version of an image they are pulling from a repository. The command to tag an image is **docker tag** and you need to provide the image ID and your chosen tag (including the repository). For example:
```docker tag 0e5574283393 username/my_repo:1.0```
- **Pulling a new image from a Docker Registry:** To pull an image from a registry, use  **docker pull**  and specify the repository name. By default, the latest version of the image is retrieved from the Docker Hub registry, but this behaviour can be overridden by specifying a different version and/or registry in the pull command. For example, to pull version 2.0 of my_repo from a private registry running on localhost port 5000, run:
```docker pull localhost:5000/my_repo:2.0```
- **Pushing a local image to the Docker registry:** You can push an image to Docker Hub or another registry to make it available for other users by running the docker push command. For example, to push the (latest) local version of my_repo to Docker Hub, make sure you’re logged in first by running **docker login**, then run:
```docker push username/my_repo```
- **Searching for images:** You can search the Docker Hub for images relating to specific terms using **docker search**.  You can specify filters to the search, for example only list “official” repositories.
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

```$ docker images```

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
- **Google Container Engine:** Google Container Engine, built on Kubernetes, lets you run Docker containers on the Google Cloud.
- **Kubernetes:** An orchestration system for Docker containers. It handles scheduling and manages workloads based on user-defined parameters.
- **Mesosphere Marathon:** Marathon is a container orchestration framework for Apache Mesos that is designed to launch long-running applications.
- **Amazon ECS:** The ECS supports Docker containers and lets you run applications on a managed cluster of Amazon EC2 instances.
- **Azure Container Service (ACS):** ACS lets you create a cluster of virtual machines that act as container hosts along with master machines that are used to manage your application containers.
- **Cloud Foundry’s Diego:** Container management system that combines a scheduler, runner, and health manager.
- **CoreOS Fleet:** Container management tool that lets you deploy Docker containers on hosts in a cluster as well as distribute services across a cluster.

![image](https://user-images.githubusercontent.com/29313557/114074050-96bcd580-98c1-11eb-9849-3cbaad6249ac.png)

  
  ## Kubernetes
  

