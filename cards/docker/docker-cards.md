<!-- title:Docker -->

<!-- Card Start -->
### Front
What is a Docker Container?

### Back
A Docker Container is a lightweight, standalone executable package of software that includes everything needed to run an application: code, runtime, system tools, libraries, and settings. Containers isolate applications, ensuring consistent environments across development, testing, and production.

<!-- Card End --> 
<!-- Card Start -->
### Front
What is a Docker Image?

### Back
A Docker Image is an immutable file that contains the source code, libraries, dependencies, tools, and other files needed for an application to run. Containers are created from Docker images.

<!-- Card End --> 
<!-- Card Start -->
### Front
Explain the difference between Docker Images and Docker Containers.

### Back
Docker Images: Read-only templates used to create containers.
Docker Containers: Runtime instances created from images, each providing isolated application environments.


<!-- Card End --> 

<!-- Card Start -->

### Front
What is a Dockerfile?

### Back
A Dockerfile is a text-based script used to define and automate the steps to create a Docker image. It includes instructions to install dependencies, copy files, set environment variables, and execute commands.

<!-- Card End --> 
<!-- Card Start -->
### Front

List important Dockerfile commands to memorize.

### Back
- FROM: Base image to build upon.

- RUN: Executes shell commands during build.

- CMD: Default command executed when container starts.

- ENTRYPOINT: Defines a container's executable.

- COPY: Copies files from the host to the image.

- ADD: Similar to COPY, but supports extraction and remote URLs.

- EXPOSE: Specifies network ports at runtime.

- ENV: Sets environment variables.

- WORKDIR: Sets the working directory inside the container.

<!-- Card End --> 
<!-- Card Start -->
### Front
What does the Docker command docker run -d -p 8080:80 myimage do?

### Back
Runs a Docker container from the image myimage in detached mode (-d), mapping port 80 inside the container to port 8080 on the host machine (-p 8080:80).

<!-- Card End --> 
<!-- Card Start -->
### Front
Explain the Docker concepts of Volumes and their purpose.

### Back
Volumes in Docker are persistent data storage mechanisms that remain accessible even after containers are deleted. They allow sharing data between containers or between the container and host, providing persistence and data durability.

<!-- Card End --> 
<!-- Card Start -->
### Front
What is Docker Compose?

### Back
Docker Compose is a YAML-based configuration tool for defining and running multi-container Docker applications. It allows orchestrating multiple containers, specifying dependencies, networking, and volumes easily.

<!-- Card End --> 
<!-- Card Start -->
### Front
Provide a basic example of a Docker Compose file.

### Back
yaml
Copy
Edit
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: examplepass
<!-- Card End --> 
<!-- Card Start -->
### Front
What is a Docker Registry and give an example?

### Back
A Docker Registry is a centralized location where Docker images can be stored and shared. Examples include Docker Hub (public), AWS ECR, Google Container Registry, and private Docker registries.

<!-- Card End --> 
<!-- Card Start -->
### Front
Explain Docker Networking briefly.

### Back
Docker Networking enables containers to communicate with each other and with external networks. Docker provides several networking options such as:

**Bridge** (default isolated network)

**Host** (shares the host’s network stack)

**None** (disables networking)

**Overlay** (multi-host networking)

**Macvlan** (assigns unique MAC addresses to containers)

<!-- Card End --> 
<!-- Card Start -->
### Front
What is Docker Swarm?

### Back
Docker Swarm is Docker's native clustering and orchestration tool. It allows multiple Docker engines to collaborate as a single virtual Docker host, enabling load balancing, scalability, and resilience for containerized applications.

<!-- Card End --> 
<!-- Card Start -->
### Front
What are some key commands to manage Docker containers?

### Back
docker ps: Lists running containers.
docker ps -a: Lists all containers (including stopped).
docker start <container>: Starts an existing stopped container.
docker stop <container>: Gracefully stops a running container.
docker rm <container>: Removes a container.
docker logs <container>: Views logs for a container.
<!-- Card End --> 
<!-- Card Start -->
### Front
What is the purpose of .dockerignore file?

### Back
A .dockerignore file specifies patterns to exclude files and directories from the Docker build context, similar to .gitignore. It reduces image size and build time by ignoring unnecessary files.

<!-- Card End --> 
<!-- Card Start -->
### Front
How can you debug or troubleshoot Docker containers?

### Back
Common Docker debugging commands include:

`docker logs <container>`: Inspect container logs.

`docker exec -it <container> /bin/bash`: Get an interactive shell inside a running container.

`docker inspect <container>`: Detailed container metadata and configuration.

`docker stats`: Real-time resource usage of running containers.

<!-- Card End --> 
<!-- Card Start -->

### Front
Explain Docker layers briefly.

### Back
Docker Images are composed of layers, each created by Dockerfile commands. Layers are cached, reusable, and immutable. This layering mechanism optimizes storage and speeds up image building by reusing unchanged layers.

 
#### **Understanding Docker Layers**
A **Docker image** is built up from multiple **layers**. Each layer represents an instruction in the `Dockerfile`, and together they form the final image.

1. **Layers are Created by Dockerfile Commands**  
   - Every command in a `Dockerfile` (except `FROM`) creates a new layer.  
   - For example, these commands add layers:
     ```Dockerfile
     FROM ubuntu:latest  # Base image (creates the first layer)
     RUN apt-get update && apt-get install -y curl  # Creates a new layer
     COPY myfile.txt /app/  # Creates another layer
     ```

2. **Layers are Cached**  
   - When you rebuild an image, Docker **reuses** layers that haven't changed.  
   - If you modify a command, only that layer and subsequent layers need to be rebuilt, saving time.  

3. **Layers are Reusable**  
   - If multiple images use the same base image or similar steps, Docker can reuse the existing layers instead of downloading/building them again.

4. **Layers are Immutable**  
   - Once created, a layer **cannot be modified**.  
   - If a command changes, Docker creates a **new layer**, and the old one remains in the cache (until cleaned up).

### **Optimization Tip**
- **Place frequently changing instructions at the bottom** of your `Dockerfile` to maximize caching.
- **Use multi-stage builds** to reduce image size.

 

<!-- Card End -->


















<!-- Card Start -->
### Front
What is the command to prune unused Docker resources (containers, networks, images, caches)?

### Back
```bash

docker system prune
```

This command removes all unused containers, networks, dangling images, and build caches to free up disk space.

<!-- Card End --> 
<!-- Card Start -->

### Front
How do you build a Docker image with a specific name and tag from a Dockerfile?

### Back

```bash

docker build -t myimage:tagname .
```

-t specifies the name and tag of the image.
. indicates the build context (current directory).
<!-- Card End --> 

<!-- Card Start -->

### Front
What is the difference between CMD and ENTRYPOINT in a Dockerfile?

### Back

**CMD**: Specifies default arguments or commands to run. Easily overridden at runtime.

**ENTRYPOINT**: Defines the container’s executable; arguments passed at runtime append to this entrypoint.

Using both together is common to allow parameterized execution:

```Dockerfile

ENTRYPOINT ["python", "app.py"]
CMD ["--help"]
```


<!-- Card End --> 
<!-- Card Start -->

### Front
How can you list all Docker networks on your system?

### Back

```bash

docker network ls
```

<!-- Card End --> 
<!-- Card Start -->

### Front
How do you inspect detailed metadata about a Docker container?

### Back
```bash

docker inspect <container_id_or_name>
```

This command returns detailed JSON metadata including container configuration, networking, mounts, and state.

<!-- Card End --> 
<!-- Card Start -->

### Front
What command allows you to copy files from your host into a running Docker container?

### Back
```bash

docker cp localfile.txt <container_id>:/path/in/container/
```

Copies files or folders into a running container.

<!-- Card End --> 
<!-- Card Start -->
### Front
What is Docker's multi-stage build feature and why use it?

### Back
A multi-stage build allows using multiple FROM statements in a Dockerfile, creating intermediate build stages.
This helps create smaller final images by discarding unnecessary build artifacts, compilers, or development dependencies.

Example snippet:

```Dockerfile
 
FROM node AS builder
WORKDIR /app
RUN npm install && npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
```

<!-- Card End --> 
<!-- Card Start -->
### Front
What CLI command restarts a running Docker container?

### Back

```bash
docker restart <container_id_or_name>
```

This stops and then immediately restarts a running container.

<!-- Card End -->
<!-- Card Start -->
### Front
How do you view real-time resource usage stats for running Docker containers?

### Back

```bash
docker stats
```

This provides a live summary of CPU, memory, network, and I/O metrics for running containers.

<!-- Card End --> 
<!-- Card Start -->

### Front
What's the difference between Docker Hub and Docker Registry?

### Back

Docker Hub: Publicly available hosted registry managed by Docker Inc.
Docker Registry: General term for Docker's open-source component or self-hosted registry services (e.g., Nexus, Harbor).
Docker Hub is an instance of Docker Registry provided as a service.

<!-- Card End --> 
<!-- Card Start -->

### Front
Explain Docker secrets briefly.

### Back
Docker secrets securely store and manage sensitive data (passwords, API keys, certificates) within Docker Swarm clusters. Secrets are encrypted at rest and in transit, and containers access them as files mounted at /run/secrets/.

Example usage:

```bash
docker secret create db_password secret.txt
```

<!-- Card End --> 
<!-- Card Start -->
### Front
How do you scale services with Docker Compose?

### Back

```bash
docker-compose up -d --scale service_name=3
```

This scales the specified service to run multiple container instances simultaneously.
<!-- Card End --> 

<!-- Card Start -->

### Front
What command shows the Docker container’s currently exposed ports?

### Back
```bash
docker port <container_id_or_name>
```

Shows port mappings for a container, for example:

```bash
80/tcp -> 0.0.0.0:8080
```

<!-- Card End --> 
<!-- Card Start -->

### Front
Explain Docker's bind mounts vs volumes.

### Back
Bind Mounts: Directly link host directories or files to containers. Ideal for development due to immediate host-container synchronization.
Volumes: Docker-managed storage, isolated from host filesystem structure, ensuring persistent, portable, and easily manageable data storage.

<!-- Card End --> 
<!-- Card Start -->

### Front
What Docker command allows tagging and pushing an image to a Docker Registry?

### Back
Tagging an existing image:

```bash
docker tag localimage:latest username/repo:tag
```

Pushing to registry:

```bash
docker push username/repo:tag
```

Typically used for sharing images via Docker Hub or private registries.

<!-- Card End -->