# Dockerfile
- The Dockerfile is used by the docker build command to create a docker image
# Docker Image
- An image is an immutable and read-only lightweight, standalone executable package
- Includes code, runtime, libraries, environment variables, config files and everything needed to run a piece of software
- If you want to modify it, you must modify the dockerfile and create a new docker image
# Docker Container
- Runtime instance of a docker image
- Completely isolated from the host and other containers, has its own file system and can be started, stopped and deleted independently 

# Persistence
- Created to connect the container file system with the host, enabling persistence
## Container Volumes
- Creates a docker volume to store data that can be utilized by docker containers
- When running a container, specify a `--mount` option to specify a volume mount
- Best use case is for storing container data that must persist beyond the existence of the container
- Docker will choose host location for the volume
- Can populate new volume with container contents
## Bind Mounts
- Bind mounts can bind specific files or directories on the host to the container
- Best use case is source code, live coding without the need to recreate images and containers

# Container Networking
- Allow isolated containers to communicate with each other

# Docker Compose
- You can define the application stack in a file, makes it easy to reproduce all the networks and settings created 
- Uses the `compose.yaml` in the same root directory as the `Dockerfile`
```yaml
services:
  app:
    image: node:lts-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 127.0.0.1:3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos
```
- `services`(or containers) to add all the necessary containers that will be used, the container name will automatically become a network alias
- `image` the image to build the container
- `command`: normally placed close to the image definition, although there is no order requirement
- `ports` for the port mapping 
- `working_dir` working directory on the container 
- `volumes` mappings for persistence, can be relative paths. This case is using a bind mount for the source code
- `environment` the environment variables definitions
```yaml
services:
  app:
    # The app service definition
  mysql:
    image: mysql:8.0
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```
- `volumes` on the top-level will create a volume that can be specified on the service config
    - Compose will not automatically create a volume, contrary to `docker run`

# Image Layer Caching
- Supporting the caching of dependencies by copying only dependency files first, running yarn install, and then copying in everything else, for example
- This will allow faster builds and pushing and pulling of images because a build step will already be cached and will not need to be executed again

# Multi-stage builds
- Can separate build-time dependencies from runtime dependencies
- Reduces overall image size by shipping only what your app needs to run
- Can use a build step first using necessary environments and then just copy the created files into another more basic environment, since it does not need the resources need to build in order to run