# Container
Containerization is a technique that allows software to run reliably regardless of the computing environment. By encapsulating software within isolated environments called containers
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


  
  ## Kubernetes
  

