# Docker

![](<../.gitbook/assets/Untitled (1).png>)

![](<../.gitbook/assets/Untitled (1) (1).png>)

Image naming structure : `remote_location/username/image_name` | ex : `docker.io/nginx/nginx`

## Docker basic commands

* remove container
  * `docker rm -vf $(docker ps -a -q)`
* remove all images
  * `docker rmi -f $(docker images -a -q)`
* runs the container from image, gets it from the docker hub
* if not found locally
  * `docker run [image]`
* to list info of containers, -a for more
  * `docker ps [-a]`
* stop running container
  * `docker stop [container]`
* remove container
  * `docker rm [container]`
* list all images
  * `docker images`
* remove the image, note all container running of this image
* should be removed first
  * `docker rmi [image name]`
* to download image from remote, not run it immediately
  * `docker pull`
* docker stop is no process is running, sleep will delay the stop process\`
  * `docker run [container] sleep 5`
* to execute a process inside a docker container
  * `docker exec [container] [command to run]`
* to run the docker in de-attach mode, that means it will be in put in background
  * `docker run -d [container]`
* to attach to the output of the container
  * `docker attach [container]`
  * `docker run [container]:[version]`
* to interact with the terminal of the container, only input
  * `docker run -i [container]`
* to interact with the terminal of the container, both input and output
  * `docker run -it [container]`
* to attach you system's port to the port open inside the container
  * `docker run -p 80:5000 [container]`
* create new volume
  * `docker volume create data_volume`
* to save persistent data on disk for it to not get deleted in case the container is deleted
  * path to directory on your system : ex : `/opt/datadir`
  * path to directory on the container : ex : `/var/lib/mysql`&#x20;

```
docker run -v \
  [path to directory on your system]:[path to directory on the container] \
 [container]

docker run -v [volume name]:[path to directory on the container] [container]

# or

docker run \
	--mount type=bind,source=[volume],target=[volume insider container] \
	[container name]
```

* to get info about a container in JSON format
  * `docker inspect [container]`
* to get logging info
  * `docker logs [container]`
* to specify environment variable when running a container
  * `docker run -e [ENV_KEY]=[ENV_VALUE] [container]`



![](<../.gitbook/assets/Untitled (2) (1).png>)

#### Steps to create your own images

Create a file name `Dockerfile`

* specify OS
* update the packages of OS
* install dependency using apt
* install python dependencies using pip
* copy source code into the image
* start the process

This instructions take place in layered architecture, changes made to one layer will only effect the same layer in the next build

To get all info about build : `docker history [image]`

```bash
#  to build the image
docker build Dockerfile -t [tag name]

# to save img to remote
docker push [tag name]
```

Sample `Dockerfile`

```bash
FROM [os]

RUN [some command]

COPY [code]

ENTYRPOINT [instruction to start the process]
```

## Networking in Docker

![](<../.gitbook/assets/Untitled (3) (1).png>)

There are 3 network in docker

* Bridge : network within the docker host, for inter-container communication
* Host : network to expose the containers to the OS
* None : specify `--network=none`

**You can find bridge network info for a given container using inspect command**

To create custom bridge ( user defined network )

```bash
docker network create \\
	--driver bridge \\
	--subnet[subnet]/16 
	[bridge network name]

# to list all network
docker network ls
```

![](<../.gitbook/assets/Untitled (4).png>)

## Embedded DNS

Docker host contains a internal DNS resolver for different containers to communicate to each other. In place of URL, just add the name of the container you want to communicate to.

![](<../.gitbook/assets/Untitled (5) (2).png>)
