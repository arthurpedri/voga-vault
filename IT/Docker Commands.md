`docker ps --all`
- Lists all docker containers, including stopped containers

`docker context ls/use <container-name>`
- Lists all contexts or chooses another context to use

`docker build -t <image-name> <directory>`
- Builds an image based on the dockerfile in the directory
- `-t` will tag the image with a human readable name

`docker run -d -p 127.0.0.1:3000:3000 <image-name>`
- Runs image in container
- `-d` will detach the container and run it in the background
- `-p` will publish the container to create a port mapping between the container and the host

`docker stop <container-id>`
- Stops the container with matching id

`docker rm <container-id>`
- Removes container with matching id
- `-f` will force a stop and remove the container

`docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=<volume-name>,target=<container mount point> <image-name>`
- `--mount` will specify a volume mount to a target, for example `/etc/todos`
- For named volumes: `type=volume,src=my-volume,target=/usr/local/data`
- For bind mounts: `type=bind,src=/path/to/data,target=/usr/local/data`

`docker network create <network-name>`
- Creates a network to allow container interaction
```sh
docker run -d \
    --network todo-app --network-alias mysql \
    -v todo-mysql-data:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=secret \
    -e MYSQL_DATABASE=todos \
    mysql:8.0
```
- Connects to network with an alias for the container
- Attaches (and automatically creates) a volume 
- Sets environment variables for the container

`docker exec -it <container> sh`
- `-i` interactive flag
- `-t` terminal flag
- `sh` to open a command line on the container

`docker compose up -d`
- Creates everything necessary for the compose specification and runs the containers

`docker compose down --volumes`
- Stops and deletes all compose containers
- `--volumes` will also delete the volumes, which are not deleted by default

