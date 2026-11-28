# Module 7 - Containers with Docker

Module 7 is about Docker and containerization. 

Docker is an open source containerization platform that allows developers to package applications with all their dependencies & configurations into containers, avoiding manual installs and making development and deployment more efficient. Container artifacts are stored in container repos, e.g. dockerhub. Allows devs & ops to work together to package the application in a container with no environment config needed except container runtime. Only one command to install apps, and possible to run multiple versions of apps with no conflicts. Both VMs and Containers are virtualization technologies but containers are more efficient than VMs - faster, smaller. Important to use lean base Linux images to support this. Docker Compose is a tool for defining and running multiple docker containers, using yaml. There are a number of docker best practices to follow to allow for better security and performance.

### Demo 1 - Container vs Image

I have installed Docker on my Windows machine, v. 4.95.0 and downloaded two versions of Postgres Docker images to my machine and run them side by side

### Demo 2 - Main Docker Commands

Pulled the latest Redis image and used the following commands:

- docker pull redis (download image)
- docker images (see what image artifacts are downloaded)
- docker run redis (starts a container with the image / claims terminal)
- docker run -d redis (starts a container with image in detached mode / always me to continue using terminal)
- docker ps (see running containers and associated images and other info)
- docker stop <id>
- docker start <id>
- docker ps -a (all containers running or not running)
- docker run -p 6000:6379 redis (bind laptop port to container port -- can use to run multiple redis images bound to different ports)
  
### Demo 3 - Debug Commands

### Demo 4 - Use Docker for local development






