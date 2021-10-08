# Docker

* Check for docker version :
  * `docker version`
* to only pull the container without running it
  * `docker pull docker/whalesay`
* To run a sample docker image
  * `docker run docker/whalesay cowsay Hello_Uday_Yadav`
* to run a version
  * `docker run redis:4.0`
* to show currently running dockers :
  * `docker ps`
  * `docker ps -a`
    * to list all that were running in the past
* to list all images
  * `docker images`
* to stop docker
  * `docker stop <name of docker without the brackets>`
* name your container
* `docker run --name my_personal_container redis`
* to remove a container
  * `docker rm <name of docker>`
* to remove docker image
  * `docker rmi <name of docker>`
* running a docker
  * `sudo docker run docker/whalesay`
* get list of all networks
* `docker network ls`
* create a network
* `docker network create <network name : yourself>`
* to connect a container to the network
* `--net <name of your network>`

  _A container is not like a **VM** that starts and keeps running, a docker will exit/stop after it has completed the task or the code running has stopped_

* to put docker into sleep
  * `docker run ubuntu sleep 5`
* to bind a container to host machine port
* `docker run -p6000:6543 <name of img>`
* :
* to execute a command on a running instance of docker

  `docker exec <name of running container> cat /etc/host`

* to run the docker in background

  `docker run -d kodekloud/simple-webapp`

  This will output a key which you should save in order to attach to it again

* to attach to a docker

  `docker attach <key>`

* To stop containers run the command

  `docker stop <container id | container name>`

* And then to delete them run

  `docker rm <container id | container name>`

* to stop docker : `docker stop key`
* to run docker but with different name

  `docker run --name webapp nginx:1.14-alpine`

* Inspect the docker config

  `docker inspect <name of docker image>`

### Networking Inside a Docker

```bash
remove container : docker rm -vf $(docker ps -a -q)
remove all iamges : docker rmi -f $(docker images -a -q)
```

name of docker and heroku app is same `.dockerignore`

`os/env` for port number

## Understanding Docker File

### CMD vs Entry Point

* `CMD [nginx]` is the command that the container will executes when it runs
  * Ex : `CMD sleep 5`
* `CMD ["command","param1"]`, `command` must be executable
* Entry Point instructions on the other hand is like arguments given while given while running the docker file, the argument gets appended to the `ENTRYPOINT`
* `ENTRYPOINT["sleep"]`, when run with `docker run ubuntu 10`, the 10 gets appended to the sleep and the container then executes the `sleep 10` command.
* If entry point is not given while running the image : it will show an error of `missing operand`
* to solve this error, you need to specify a default `CMD[]` which then in case of missing argument, gets appended to the `ENTRYPOINT`

