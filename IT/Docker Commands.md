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