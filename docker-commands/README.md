## Basic commands

1. `docker run busybox echo hi there` Runs docker container and the following is the command which will run as soon as the container starts.

PS: `docker run` = `docker create` + `docker start`

2. `docker ps` to see all containers running in the machine.
3. `docker ps --all` to see all containers ever created.
4. `docker create hello-world` create container (returns container-id)
5. `docker start -a <container-id>` start created container (-a to attach to container and listen to output)
6. `docker stop $(docker ps -aq)` stop all containers
7. `docker rm $(docker ps -aq)` remove all containers
8. `docker rmi $(docker images -q)` remove all images
9. `docker system prune` delete all containers and images
10. `docker logs <container-id>` all the logs emitted from the container
11. `docker stop <container-id>` shut down the container and clean up (if not stops in 10 seconds, fallback to kill)
12. `docker kill <container-id>` immediately shut down

## Running redis in container

1. `docker run redis`
2. `docker exec -it <container-id> redis-cli` Run docker cli (-it means stdin formatting respectively)
