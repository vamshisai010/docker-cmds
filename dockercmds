Below is a **single-page GitHub-ready Docker command script**.
Create a file like:

```bash
docker-commands-cheatsheet.md
```

Then paste the full content below.

````md
# Docker Complete Commands Script — Commands, Explanation, Use Cases, Examples

Docker is a containerization platform used to package applications with their dependencies and run them consistently across different environments such as local systems, servers, CI/CD pipelines, and cloud platforms.

---

## 1. Docker Version, Info, and Help Commands

### Check Docker version

```bash
docker --version
````

Shows the installed Docker client version.

```bash
docker version
```

Shows detailed Docker client and server version information.

### Check Docker system information

```bash
docker info
```

Shows Docker engine details like containers, images, storage driver, OS, CPU, memory, Docker root directory, and runtime.

### Get Docker command help

```bash
docker --help
```

Shows all available Docker commands.

```bash
docker container --help
docker image --help
docker volume --help
docker network --help
```

Shows help for specific Docker command groups.

---

## 2. Docker Image Commands

A Docker image is a read-only template used to create containers.

### List Docker images

```bash
docker images
```

or

```bash
docker image ls
```

Shows all local Docker images.

### List images with full details

```bash
docker image ls -a
```

Shows all images including intermediate layers.

### Pull image from Docker Hub

```bash
docker pull nginx
```

Downloads the latest nginx image.

```bash
docker pull nginx:alpine
```

Downloads a specific image tag.

Use case: Pull base images before running containers or building custom images.

### Search image from Docker Hub

```bash
docker search nginx
```

Searches Docker Hub for nginx-related images.

### Remove Docker image

```bash
docker rmi nginx
```

or

```bash
docker image rm nginx
```

Removes an image from local system.

### Force remove image

```bash
docker rmi -f nginx
```

Forcefully removes an image even if it is used by stopped containers.

### Remove image by ID

```bash
docker rmi IMAGE_ID
```

Example:

```bash
docker rmi 605c77e624dd
```

### Remove all unused images

```bash
docker image prune
```

Removes dangling images.

### Remove all unused images including unused tagged images

```bash
docker image prune -a
```

### Show image history

```bash
docker history nginx
```

Shows image layers and build history.

### Inspect image details

```bash
docker inspect nginx
```

Shows complete metadata of image in JSON format.

### Tag an image

```bash
docker tag myapp:latest username/myapp:v1
```

Creates another name/tag for the same image.

Use case: Required before pushing image to Docker Hub.

### Save image as tar file

```bash
docker save -o nginx.tar nginx
```

Saves image into a tar file.

### Load image from tar file

```bash
docker load -i nginx.tar
```

Loads image from tar file.

Use case: Move images between servers without pulling from registry.

---

## 3. Docker Container Commands

A container is a running instance of an image.

### Run container

```bash
docker run nginx
```

Creates and starts a container from nginx image.

### Run container in detached mode

```bash
docker run -d nginx
```

Runs container in background.

`-d` means detached mode.

### Run container with name

```bash
docker run -d --name mynginx nginx
```

Creates container with custom name.

### Run container with port mapping

```bash
docker run -d -p 8080:80 nginx
```

Maps host port `8080` to container port `80`.

Access using:

```bash
http://localhost:8080
```

Explanation:

```bash
-p HOST_PORT:CONTAINER_PORT
```

### Run container with interactive terminal

```bash
docker run -it ubuntu bash
```

Starts Ubuntu container and opens bash shell.

Explanation:

```bash
-i = interactive
-t = terminal
```

### Run container and remove after exit

```bash
docker run --rm ubuntu echo "Hello Docker"
```

Automatically deletes the container after command finishes.

Use case: Temporary testing.

### Run container with environment variable

```bash
docker run -d -e MYSQL_ROOT_PASSWORD=root mysql
```

Passes environment variable into container.

### Run container with multiple environment variables

```bash
docker run -d \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=mydb \
  -e MYSQL_USER=admin \
  -e MYSQL_PASSWORD=admin123 \
  mysql
```

### Run container with volume mount

```bash
docker run -d -v myvolume:/data nginx
```

Mounts Docker volume to container path `/data`.

### Run container with bind mount

```bash
docker run -d -v /home/user/app:/app nginx
```

Mounts host directory into container.

### Run container with current directory mount

```bash
docker run -it -v $(pwd):/app ubuntu bash
```

Use case: Work with local files inside container.

### Run container with restart policy

```bash
docker run -d --restart always nginx
```

Restart policies:

```bash
--restart no
--restart always
--restart on-failure
--restart unless-stopped
```

Use case: Production containers should restart automatically.

### Run container with memory limit

```bash
docker run -d --memory 512m nginx
```

Limits container memory to 512 MB.

### Run container with CPU limit

```bash
docker run -d --cpus="1.5" nginx
```

Allows container to use 1.5 CPUs.

### Run container with hostname

```bash
docker run -d --hostname webserver nginx
```

Sets hostname inside container.

### Run container with custom DNS

```bash
docker run -d --dns 8.8.8.8 nginx
```

Uses custom DNS server.

### Run container in specific network

```bash
docker run -d --network mynetwork --name app nginx
```

Connects container to custom Docker network.

---

## 4. List Containers

### List running containers

```bash
docker ps
```

or

```bash
docker container ls
```

### List all containers

```bash
docker ps -a
```

Shows running, stopped, and exited containers.

### List only container IDs

```bash
docker ps -q
```

### List all container IDs

```bash
docker ps -aq
```

Use case: Useful for bulk delete or stop commands.

### Format container output

```bash
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"
```

Shows selected columns in table format.

---

## 5. Start, Stop, Restart, Kill Containers

### Start stopped container

```bash
docker start mynginx
```

### Stop running container

```bash
docker stop mynginx
```

Gracefully stops the container.

### Restart container

```bash
docker restart mynginx
```

### Kill container immediately

```bash
docker kill mynginx
```

Forcefully stops container.

Difference:

```bash
docker stop = graceful stop
docker kill = immediate stop
```

### Pause container

```bash
docker pause mynginx
```

Suspends all processes inside container.

### Unpause container

```bash
docker unpause mynginx
```

### Rename container

```bash
docker rename oldname newname
```

---

## 6. Remove Containers

### Remove stopped container

```bash
docker rm mynginx
```

### Force remove running container

```bash
docker rm -f mynginx
```

### Remove all stopped containers

```bash
docker container prune
```

### Remove all containers

```bash
docker rm -f $(docker ps -aq)
```

Use carefully. This deletes all containers.

---

## 7. Execute Commands Inside Container

### Open shell inside running container

```bash
docker exec -it mynginx bash
```

If bash is not available:

```bash
docker exec -it mynginx sh
```

### Run command inside container

```bash
docker exec mynginx ls /usr/share/nginx/html
```

### Check environment variables inside container

```bash
docker exec mynginx env
```

### Check running processes inside container

```bash
docker exec mynginx ps aux
```

---

## 8. Container Logs and Monitoring

### View container logs

```bash
docker logs mynginx
```

### Follow live logs

```bash
docker logs -f mynginx
```

### Show last 50 log lines

```bash
docker logs --tail 50 mynginx
```

### Show logs with timestamps

```bash
docker logs -t mynginx
```

### Show live resource usage

```bash
docker stats
```

### Show stats for one container

```bash
docker stats mynginx
```

### Show container processes

```bash
docker top mynginx
```

### Show container changes

```bash
docker diff mynginx
```

Shows changed files inside container.

---

## 9. Inspect Containers

### Inspect full container details

```bash
docker inspect mynginx
```

Shows JSON details like IP address, mounts, network, image, environment variables.

### Get container IP address

```bash
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mynginx
```

### Get container state

```bash
docker inspect -f '{{.State.Status}}' mynginx
```

### Get container restart count

```bash
docker inspect -f '{{.RestartCount}}' mynginx
```

---

## 10. Copy Files Between Host and Container

### Copy file from host to container

```bash
docker cp index.html mynginx:/usr/share/nginx/html/index.html
```

### Copy file from container to host

```bash
docker cp mynginx:/etc/nginx/nginx.conf ./nginx.conf
```

Use case: Backup config files or update test files.

---

## 11. Dockerfile Commands

A Dockerfile is used to build custom Docker images.

Example Dockerfile for Node.js:

```Dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### Dockerfile instructions explained

#### FROM

```Dockerfile
FROM ubuntu:22.04
```

Defines base image.

#### WORKDIR

```Dockerfile
WORKDIR /app
```

Sets working directory inside image.

#### COPY

```Dockerfile
COPY . .
```

Copies files from host to image.

#### ADD

```Dockerfile
ADD app.tar.gz /app
```

Copies files and can auto-extract tar files.

Difference:

```bash
COPY = simple file copy
ADD = copy + tar extraction + remote URL support
```

Prefer `COPY` unless `ADD` is specifically needed.

#### RUN

```Dockerfile
RUN apt update && apt install -y nginx
```

Executes command while building image.

#### CMD

```Dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

Default command when container starts.

#### ENTRYPOINT

```Dockerfile
ENTRYPOINT ["python"]
CMD ["app.py"]
```

ENTRYPOINT defines fixed executable. CMD provides default arguments.

#### EXPOSE

```Dockerfile
EXPOSE 80
```

Documents the port used by container. It does not publish the port automatically.

#### ENV

```Dockerfile
ENV APP_ENV=production
```

Sets environment variable.

#### ARG

```Dockerfile
ARG VERSION=1.0
```

Build-time variable.

#### USER

```Dockerfile
USER appuser
```

Runs container as non-root user.

#### VOLUME

```Dockerfile
VOLUME /data
```

Creates mount point.

#### LABEL

```Dockerfile
LABEL maintainer="admin@example.com"
```

Adds metadata.

---

## 12. Docker Build Commands

### Build image from Dockerfile

```bash
docker build -t myapp .
```

Explanation:

```bash
-t = tag/name image
. = current directory as build context
```

### Build image with specific Dockerfile

```bash
docker build -f Dockerfile.dev -t myapp:dev .
```

### Build image without cache

```bash
docker build --no-cache -t myapp .
```

Use case: Rebuild everything from scratch.

### Build image with build argument

```bash
docker build --build-arg VERSION=2.0 -t myapp .
```

Dockerfile:

```Dockerfile
ARG VERSION
RUN echo $VERSION
```

### Build image with tag

```bash
docker build -t username/myapp:v1 .
```

### Build image using BuildKit

```bash
DOCKER_BUILDKIT=1 docker build -t myapp .
```

BuildKit gives faster and better builds.

---

## 13. Docker Run Examples for Real Applications

### Run Nginx

```bash
docker run -d --name web -p 8080:80 nginx
```

### Run Apache

```bash
docker run -d --name apache -p 8081:80 httpd
```

### Run MySQL

```bash
docker run -d \
  --name mysql-db \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=mydb \
  -p 3306:3306 \
  mysql:8
```

### Run PostgreSQL

```bash
docker run -d \
  --name postgres-db \
  -e POSTGRES_PASSWORD=root \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  postgres
```

### Run Redis

```bash
docker run -d --name redis -p 6379:6379 redis
```

### Run MongoDB

```bash
docker run -d \
  --name mongodb \
  -p 27017:27017 \
  mongo
```

### Run Jenkins

```bash
docker run -d \
  --name jenkins \
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

Get Jenkins initial password:

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

### Run SonarQube

```bash
docker run -d \
  --name sonarqube \
  -p 9000:9000 \
  sonarqube:lts-community
```

### Run Nexus

```bash
docker run -d \
  --name nexus \
  -p 8081:8081 \
  -v nexus-data:/nexus-data \
  sonatype/nexus3
```

Get Nexus password:

```bash
docker exec nexus cat /nexus-data/admin.password
```

---

## 14. Docker Volume Commands

Volumes are used to persist data even after container deletion.

### List volumes

```bash
docker volume ls
```

### Create volume

```bash
docker volume create myvolume
```

### Inspect volume

```bash
docker volume inspect myvolume
```

### Remove volume

```bash
docker volume rm myvolume
```

### Remove unused volumes

```bash
docker volume prune
```

### Use volume with container

```bash
docker run -d -v myvolume:/data nginx
```

### Backup volume

```bash
docker run --rm \
  -v myvolume:/volume \
  -v $(pwd):/backup \
  ubuntu tar cvf /backup/backup.tar /volume
```

### Restore volume

```bash
docker run --rm \
  -v myvolume:/volume \
  -v $(pwd):/backup \
  ubuntu tar xvf /backup/backup.tar -C /
```

---

## 15. Docker Bind Mount Commands

Bind mount connects host directory to container directory.

### Bind mount example

```bash
docker run -d \
  --name web \
  -p 8080:80 \
  -v /home/user/html:/usr/share/nginx/html \
  nginx
```

Use case: Live update website files from host.

### Read-only bind mount

```bash
docker run -d \
  -v /home/user/html:/usr/share/nginx/html:ro \
  nginx
```

`ro` means read-only.

---

## 16. Docker Network Commands

Docker networks allow containers to communicate.

### List networks

```bash
docker network ls
```

Default networks:

```bash
bridge
host
none
```

### Create network

```bash
docker network create mynetwork
```

### Create bridge network

```bash
docker network create --driver bridge app-network
```

### Inspect network

```bash
docker network inspect mynetwork
```

### Remove network

```bash
docker network rm mynetwork
```

### Remove unused networks

```bash
docker network prune
```

### Run container in network

```bash
docker run -d --name app --network mynetwork nginx
```

### Connect running container to network

```bash
docker network connect mynetwork mynginx
```

### Disconnect container from network

```bash
docker network disconnect mynetwork mynginx
```

### Container-to-container communication

```bash
docker network create appnet
docker run -d --name mysql --network appnet -e MYSQL_ROOT_PASSWORD=root mysql
docker run -it --name app --network appnet ubuntu bash
```

Inside app container:

```bash
ping mysql
```

Container names work as DNS names inside same Docker network.

---

## 17. Docker Compose Commands

Docker Compose is used to manage multi-container applications.

Compose file name:

```bash
docker-compose.yml
```

or modern:

```bash
compose.yml
```

Example:

```yaml
version: "3.8"

services:
  web:
    image: nginx
    ports:
      - "8080:80"

  redis:
    image: redis
```

### Start services

```bash
docker compose up
```

### Start services in background

```bash
docker compose up -d
```

### Stop services

```bash
docker compose stop
```

### Stop and remove services

```bash
docker compose down
```

### Stop and remove volumes also

```bash
docker compose down -v
```

### Build services

```bash
docker compose build
```

### Rebuild and start

```bash
docker compose up --build
```

### View compose logs

```bash
docker compose logs
```

### Follow logs

```bash
docker compose logs -f
```

### Run command inside compose service

```bash
docker compose exec web sh
```

### List compose services

```bash
docker compose ps
```

### Restart compose service

```bash
docker compose restart web
```

### Scale service

```bash
docker compose up -d --scale web=3
```

Use case: Run multiple replicas locally.

---

## 18. Docker Registry and Docker Hub Commands

### Login to Docker Hub

```bash
docker login
```

### Logout

```bash
docker logout
```

### Tag image for Docker Hub

```bash
docker tag myapp username/myapp:latest
```

### Push image

```bash
docker push username/myapp:latest
```

### Pull pushed image

```bash
docker pull username/myapp:latest
```

### Full image push flow

```bash
docker build -t myapp .
docker tag myapp vamshisai010/myapp:v1
docker login
docker push vamshisai010/myapp:v1
```

---

## 19. Docker System Cleanup Commands

### Show Docker disk usage

```bash
docker system df
```

### Detailed disk usage

```bash
docker system df -v
```

### Remove unused containers, networks, images, build cache

```bash
docker system prune
```

### Remove everything unused including volumes

```bash
docker system prune -a --volumes
```

Warning: This deletes unused images, containers, networks, cache, and volumes.

### Remove stopped containers

```bash
docker container prune
```

### Remove unused images

```bash
docker image prune -a
```

### Remove unused volumes

```bash
docker volume prune
```

### Remove unused networks

```bash
docker network prune
```

### Remove build cache

```bash
docker builder prune
```

---

## 20. Docker Logs Troubleshooting Commands

### Check container status

```bash
docker ps -a
```

### Check why container exited

```bash
docker logs container_name
```

### Inspect exit code

```bash
docker inspect container_name --format='{{.State.ExitCode}}'
```

Common exit codes:

```bash
0   = successful exit
1   = general error
125 = docker run command error
126 = command cannot execute
127 = command not found
137 = killed, often memory issue
```

### Check container restart reason

```bash
docker inspect container_name --format='{{.State.Error}}'
```

### Check port conflicts

```bash
docker ps
```

If port is already used:

```bash
docker run -p 8081:80 nginx
```

Use another host port.

### Check container resource usage

```bash
docker stats
```

### Enter container for debugging

```bash
docker exec -it container_name sh
```

### Check files inside container

```bash
docker exec -it container_name ls -l /app
```

### Check app process

```bash
docker exec -it container_name ps aux
```

---

## 21. Docker Port Commands

### Publish one port

```bash
docker run -d -p 8080:80 nginx
```

### Publish multiple ports

```bash
docker run -d \
  -p 8080:80 \
  -p 443:443 \
  nginx
```

### Publish only localhost

```bash
docker run -d -p 127.0.0.1:8080:80 nginx
```

Accessible only from local machine.

### Random host port mapping

```bash
docker run -d -P nginx
```

`-P` publishes all exposed ports to random host ports.

### Check mapped ports

```bash
docker port container_name
```

---

## 22. Docker Environment Variable Commands

### Pass environment variable

```bash
docker run -e APP_ENV=dev myapp
```

### Pass env file

```bash
docker run --env-file .env myapp
```

Example `.env` file:

```env
APP_ENV=production
DB_HOST=mysql
DB_USER=admin
DB_PASS=admin123
```

Use case: Avoid writing many `-e` options.

---

## 23. Docker Resource Limit Commands

### Memory limit

```bash
docker run --memory 512m nginx
```

### Memory and swap limit

```bash
docker run --memory 512m --memory-swap 1g nginx
```

### CPU limit

```bash
docker run --cpus="2" nginx
```

### CPU shares

```bash
docker run --cpu-shares 512 nginx
```

### Limit PIDs

```bash
docker run --pids-limit 100 nginx
```

Use case: Prevent container from consuming full server resources.

---

## 24. Docker Security Commands

### Run container as non-root user

```bash
docker run -u 1000:1000 nginx
```

### Read-only filesystem

```bash
docker run --read-only nginx
```

### Drop Linux capabilities

```bash
docker run --cap-drop ALL nginx
```

### Add specific capability

```bash
docker run --cap-add NET_ADMIN ubuntu
```

### No new privileges

```bash
docker run --security-opt no-new-privileges nginx
```

### Run privileged container

```bash
docker run --privileged ubuntu
```

Warning: `--privileged` gives high-level host access. Avoid in production unless required.

---

## 25. Docker Login, Registry, and Private Registry

### Login to private registry

```bash
docker login registry.example.com
```

### Tag image for private registry

```bash
docker tag myapp registry.example.com/myapp:v1
```

### Push to private registry

```bash
docker push registry.example.com/myapp:v1
```

### Pull from private registry

```bash
docker pull registry.example.com/myapp:v1
```

---

## 26. Docker Context Commands

Docker context is used to manage multiple Docker endpoints.

### List contexts

```bash
docker context ls
```

### Show current context

```bash
docker context show
```

### Create context

```bash
docker context create myremote --docker "host=ssh://user@server"
```

### Use context

```bash
docker context use myremote
```

### Switch back to default

```bash
docker context use default
```

Use case: Manage remote Docker servers from local system.

---

## 27. Docker Buildx Commands

Buildx is used for advanced builds and multi-platform images.

### Check buildx version

```bash
docker buildx version
```

### List builders

```bash
docker buildx ls
```

### Create builder

```bash
docker buildx create --name mybuilder --use
```

### Build multi-platform image

```bash
docker buildx build \
  --platform linux/amd64,linux/arm64 \
  -t username/myapp:v1 \
  --push .
```

Use case: Build image for both Intel/AMD and ARM systems.

---

## 28. Docker Compose Full Example: App + MySQL

```yaml
version: "3.8"

services:
  app:
    build: .
    container_name: myapp
    ports:
      - "3000:3000"
    environment:
      DB_HOST: mysql
      DB_USER: root
      DB_PASSWORD: root
      DB_NAME: mydb
    depends_on:
      - mysql
    networks:
      - appnet

  mysql:
    image: mysql:8
    container_name: mysql-db
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: mydb
    volumes:
      - mysql-data:/var/lib/mysql
    networks:
      - appnet

volumes:
  mysql-data:

networks:
  appnet:
```

Run:

```bash
docker compose up -d --build
```

Stop:

```bash
docker compose down
```

Stop and remove database volume:

```bash
docker compose down -v
```

---

## 29. Dockerfile Best Practices

### Use small base images

```Dockerfile
FROM node:18-alpine
```

Smaller images are faster and more secure.

### Use `.dockerignore`

Example `.dockerignore`:

```gitignore
node_modules
.git
.env
logs
dist
target
```

Prevents unnecessary files from entering image build context.

### Combine RUN commands

Bad:

```Dockerfile
RUN apt update
RUN apt install -y nginx
```

Good:

```Dockerfile
RUN apt update && apt install -y nginx && rm -rf /var/lib/apt/lists/*
```

Reduces image layers and size.

### Use non-root user

```Dockerfile
RUN adduser -D appuser
USER appuser
```

Improves container security.

### Pin image versions

Bad:

```Dockerfile
FROM node:latest
```

Good:

```Dockerfile
FROM node:18-alpine
```

Avoids unexpected breaking changes.

---

## 30. Common Docker Problems and Fixes

### Problem: Docker daemon not running

Error:

```bash
Cannot connect to the Docker daemon
```

Fix:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Check status:

```bash
sudo systemctl status docker
```

### Problem: Permission denied while using Docker

Error:

```bash
permission denied while trying to connect to Docker daemon socket
```

Fix:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

Then logout/login.

### Problem: Port already allocated

Error:

```bash
Bind for 0.0.0.0:8080 failed: port is already allocated
```

Fix:

```bash
docker ps
docker stop container_name
```

or use another port:

```bash
docker run -p 8081:80 nginx
```

### Problem: Container exits immediately

Check logs:

```bash
docker logs container_name
```

Check command:

```bash
docker inspect container_name
```

Run interactively:

```bash
docker run -it image_name sh
```

### Problem: Image build fails due to missing Dockerfile

Error:

```bash
unable to evaluate symlinks in Dockerfile path: no such file or directory
```

Fix:

```bash
ls
```

Make sure Dockerfile exists in current directory.

Build from correct directory:

```bash
cd project-folder
docker build -t myapp .
```

Or specify Dockerfile path:

```bash
docker build -f path/to/Dockerfile -t myapp .
```

### Problem: Container cannot connect to database

Fix: Put both containers in same network.

```bash
docker network create appnet
docker run -d --name mysql --network appnet -e MYSQL_ROOT_PASSWORD=root mysql
docker run -d --name app --network appnet myapp
```

Use database hostname as container name:

```bash
DB_HOST=mysql
```

### Problem: Changes lost after container deletion

Reason: Data was stored inside container filesystem.

Fix: Use volume.

```bash
docker run -v mysql-data:/var/lib/mysql mysql
```

---

## 31. Important Docker Command Options

### `-d`

```bash
docker run -d nginx
```

Runs container in background.

### `-it`

```bash
docker run -it ubuntu bash
```

Interactive terminal.

### `--name`

```bash
docker run --name web nginx
```

Assigns container name.

### `-p`

```bash
docker run -p 8080:80 nginx
```

Maps host port to container port.

### `-v`

```bash
docker run -v volume_name:/path nginx
```

Mounts volume or host directory.

### `-e`

```bash
docker run -e KEY=value image
```

Passes environment variable.

### `--rm`

```bash
docker run --rm ubuntu echo hello
```

Removes container after exit.

### `--network`

```bash
docker run --network appnet nginx
```

Connects container to network.

### `--restart`

```bash
docker run --restart always nginx
```

Controls restart behavior.

### `--entrypoint`

```bash
docker run --entrypoint sh nginx
```

Overrides image entrypoint.

### `--pull`

```bash
docker run --pull always nginx
```

Always pulls latest image before running.

---

## 32. Useful One-Line Docker Commands

### Stop all running containers

```bash
docker stop $(docker ps -q)
```

### Remove all containers

```bash
docker rm -f $(docker ps -aq)
```

### Remove all images

```bash
docker rmi -f $(docker images -q)
```

### Remove all unused data

```bash
docker system prune -a --volumes
```

### Show container names only

```bash
docker ps --format "{{.Names}}"
```

### Show container IPs

```bash
docker inspect -f '{{.Name}} - {{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)
```

### Restart all running containers

```bash
docker restart $(docker ps -q)
```

### View logs of all compose services

```bash
docker compose logs -f
```

---

## 33. Docker Real-Time Use Cases

### Use case 1: Run static website using nginx

```bash
docker run -d \
  --name static-site \
  -p 8080:80 \
  -v $(pwd):/usr/share/nginx/html \
  nginx
```

### Use case 2: Run local database for development

```bash
docker run -d \
  --name dev-mysql \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=devdb \
  -p 3306:3306 \
  -v mysql-data:/var/lib/mysql \
  mysql:8
```

### Use case 3: Test commands in Ubuntu container

```bash
docker run -it --rm ubuntu bash
```

### Use case 4: Run Jenkins for CI/CD practice

```bash
docker run -d \
  --name jenkins \
  -p 8080:8080 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

### Use case 5: Run application with Dockerfile

```bash
docker build -t myapp .
docker run -d --name myapp-container -p 3000:3000 myapp
```

### Use case 6: Push image to Docker Hub

```bash
docker build -t myapp .
docker tag myapp vamshisai010/myapp:v1
docker login
docker push vamshisai010/myapp:v1
```

### Use case 7: Debug failed container

```bash
docker ps -a
docker logs container_name
docker inspect container_name
docker run -it image_name sh
```

---

## 34. Docker Command Flow for DevOps Project

Typical workflow:

```bash
git clone https://github.com/user/project.git
cd project
docker build -t myapp .
docker run -d --name myapp -p 3000:3000 myapp
docker logs -f myapp
docker tag myapp username/myapp:v1
docker login
docker push username/myapp:v1
```

In CI/CD pipeline:

```bash
docker build -t username/myapp:$BUILD_NUMBER .
docker push username/myapp:$BUILD_NUMBER
docker run -d -p 3000:3000 username/myapp:$BUILD_NUMBER
```

---

## 35. Docker Commands Summary Table

| Task                    | Command                       |
| ----------------------- | ----------------------------- |
| Check Docker version    | `docker --version`            |
| Show Docker info        | `docker info`                 |
| Pull image              | `docker pull nginx`           |
| List images             | `docker images`               |
| Build image             | `docker build -t myapp .`     |
| Run container           | `docker run nginx`            |
| Run in background       | `docker run -d nginx`         |
| Run with port           | `docker run -p 8080:80 nginx` |
| List running containers | `docker ps`                   |
| List all containers     | `docker ps -a`                |
| Stop container          | `docker stop name`            |
| Start container         | `docker start name`           |
| Restart container       | `docker restart name`         |
| Remove container        | `docker rm name`              |
| Remove image            | `docker rmi image`            |
| View logs               | `docker logs name`            |
| Enter container         | `docker exec -it name sh`     |
| List volumes            | `docker volume ls`            |
| List networks           | `docker network ls`           |
| Compose up              | `docker compose up -d`        |
| Compose down            | `docker compose down`         |
| Cleanup                 | `docker system prune`         |

---

## 36. Interview-Level Docker Points

Docker solves the problem of environment mismatch.

Example:

```bash
It works on my machine but not on server.
```

Docker fixes this by packaging:

```bash
Application code
Runtime
Libraries
Dependencies
Environment variables
Configuration
```

### Image vs Container

```bash
Image     = template/package
Container = running instance of image
```

### Volume vs Bind Mount

```bash
Volume     = managed by Docker
Bind mount = host path directly mounted
```

### CMD vs ENTRYPOINT

```bash
CMD        = default command, can be overridden
ENTRYPOINT = fixed executable, harder to override
```

### COPY vs ADD

```bash
COPY = normal copy
ADD  = copy + extract tar + remote URL support
```

### EXPOSE vs -p

```bash
EXPOSE = documentation inside Dockerfile
-p     = actual port publishing
```

### docker stop vs docker kill

```bash
docker stop = graceful shutdown
docker kill = force shutdown
```

---

## 37. Production Best Practices

Use:

```bash
Specific image tags
Non-root users
Small base images
Health checks
Volumes for persistent data
Custom networks
Resource limits
Restart policies
Secrets management
Docker Compose for multi-container setup
CI/CD pipeline for build and push
```

Avoid:

```bash
latest tag in production
Running as root
Storing data inside container
Using privileged mode unnecessarily
Putting passwords directly in Dockerfile
Large images
Unused images and containers
```

---

## 38. Final Docker Practice Project

### Project: Nginx custom website

Create `index.html`:

```html
<h1>Hello from Docker</h1>
<p>This is my Docker practice project.</p>
```

Create Dockerfile:

```Dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Build image:

```bash
docker build -t my-nginx-site .
```

Run container:

```bash
docker run -d --name mysite -p 8080:80 my-nginx-site
```

Check:

```bash
docker ps
docker logs mysite
```

Open browser:

```bash
http://localhost:8080
```

Push to Docker Hub:

```bash
docker tag my-nginx-site vamshisai010/my-nginx-site:v1
docker login
docker push vamshisai010/my-nginx-site:v1
```

Remove container:

```bash
docker rm -f mysite
```

Run from Docker Hub:

```bash
docker run -d --name mysite -p 8080:80 vamshisai010/my-nginx-site:v1
```

---

# End of Docker Complete Commands Script

```

Use `.md` extension for GitHub because it gives proper headings, code blocks, tables, and syntax highlighting.
```

