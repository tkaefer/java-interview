# Docker Concepts
  ## Images
- Images are read as templates used to create containers.
- Images are created with the docker build command, either by us or by other docker users.
- Images are composed of layers of other images.
- Images are stored in Docker registry.
 
 ## Containers
 - If an image is a class, then a container is an instance of a class - a runtime object.
 - Containers are lightweight and portable encapsulations of an environment in which to run programs.
 - Containers are created from images. Inside a container, it has all the binaries and dependencies needed to run the application.

 ## Registries and Repositories
 - A registry is where we store our images.
 - You can host your own registry, or you can use Docker public registry which is called DockerHub.
 - Inside a registry, images are stored repositories.
 - Docker repository is a collection of different docker images with the same name, that have different tags, each tag usually means a different version of the image.
 - DockerHub is a popular service for repositories.
 - Official names are reviewed by DockerHub.
 - If you don't specify a tag, it defaults to latest.
 - Docker will use the local image first if it's available, otherwise it will download it from the network.
