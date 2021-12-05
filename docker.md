Docker:
* Docker engine - tool installed on a laptop
* Docker container - aka running instance of virtual machine
* Docker image - iso of virtual machine
* Dockerfile - personal configuration of docker image

Commands:
* docker pull
* docker images
* docker run (-it/d) (-p port_local:port_docker) image_name - start container (in interactive mode/daemon) (port forwarding)
* docker exec -it container_id shell - execute container
* docker ps (-a) - current (all) containers
* docker search name
* docker rm container
* docker rmi image
* docker build -t name:version path - build a image from a Dockerfile
* docker tag image:version image:anyghing - copy image
* docker commit container_id image_name:image_tag - create new image out of container

Docker-compose - file with description of the desired containers
