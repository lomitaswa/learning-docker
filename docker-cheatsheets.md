# Docker Commands Cheatsheet

1. Get the docker Client and Server version
    * `docker version`
2. Start a container
    * `docker run <image>`
3. docker run = docker create + docker start
    * `docker create` \- Puts the image snapshot in the container\.
    * `docker start` \- Executes the start command in the container\.
4. Build an image
    * `docker build .`
    * Here the period `.` in the end represents the build context.
    * To tag an image we can use -t flag.
        * `docker build -t <username>/<image-name>:tag`
        * `docker build -t lomitaswa/frontend:latest`
5. Docker images
    * `docker images` - list docker images
    * `docker images -a` - list all docker images
    * `docker rmi <imageId>` - Remove image
6. Docker containers
    * `docker ps` \- gets current running containers\.
    * `docker ps -a` \- gets all containers\.
    * `docker rm <containerId>` - remove a container
7. Overriding a docker default command
    * `docker run hello-world echo hi there` \- This command fails\, as echo command is not there in the hello\-world container
    * `docker run busybox echo hi there` \- This command works because echo command is present in the busybox container\.
8. Remove stopped containers.
    * `docker system prune`
9. Log from container
    * `docker logs <containerId>` \- Outputs the log from the container
10. Stopping a container
    * `docker stop <containerId>` \- It sends a H/W signal <b>SIGTERM</b> to stop the container in it's own time after it finishes the job. If it doesn't stop after 10 seconds then docker fallsback to the kill command.
    * `docker kill <containerId>` \- It sends a H/W signal <b>SIGKILL</b> to kill the process immediately.
11. Execute external commands inside a container
    * `docker exec -it <containerId> <command>`
    * e.g. `docker exec -it <containerId> redis-cli`
    * `docker exec -it <containerId> sh` \- gives access to shell inside the container\.
    * Here -it is most important. It can help in taking input.
    * Every process running inside a Linux machine has 3 communication chennel attached to it.
        * STDIN
        * STDOUT
        * STDERR
12. Volume & port
    * `docker run -p <host-port>:<container-port> -v <host-volume>:<container-volume> image-name`
    * <b>-p</b> is the port which we attach to the container.
    * <b>-v</b> voluem we're attaching to the container.
    * e.g. `docker run -p 2000:3000 -v $(pwd):/app lomitaswa/frontend:latest`
13. Dockerfile
    * `docker build .` - by default **Dockerfile** is the name which is used to build an image.
    * `docker build -f Dockerfile.dev .`
        * <b>-f</b> is used to build image with different filename or special file.
14. docker-compose
    * `docker-compose up` - process the docker-compose.yml file and up all the services.
    * `docker-compose down` - stop and remove all containers
15. Push to dockerhub
    * `docker push <dockerhub-username>/<image-name>:tag`
    * `docker push lomitaswa/frontend:1.2`
