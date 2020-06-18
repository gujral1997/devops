# Steps to setup Jenkins on ec2:

## Steps to create EC2 instance

1. Create EC2 Instance(Ubuntu 16.04, 20 GB SSD, rest are default) and open 8080 port under the inbound rules of the security group of which the instance is part of.
2. Connect to the ec2 instance using ssh.

## Steps to install Docker

1. `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
2. `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"`
3. `sudo apt-get update`
4. `apt-cache policy docker-ce`
5. `sudo apt-get install -y docker-ce`
6. `sudo systemctl status docker`

## Steps to install jenkins

1. `sudo mkdir -p /var/jenkins_home`
2. `sudo chown -R 1000:1000 /var/jenkins_home/`
3. `docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home --name jenkins -d jenkins/jenkins:lts`
4. Open http://EC@-instance-public-IP:8080/ and setup the jenkins user.

## Steps to run the jenkins in container

1. run `docker ps -a` to check whether jenkins image is running. If not, run `docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home --name jenkins -d jenkins/jenkins:lts`.
2. Then copy this repository's directory (`jenkins-docker`) in the `$HOME`.
3. Then run `docker build -t jenkins-docker .`
4. We don't need the old image now Stop and remove the old image using `docker stop jenkins` and `docker rm jenkins` respective.
5. Run the new container using `docker run -p 8080:8080 -p 50000:50000 -v /var/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock --name jenkins -d jenkins-docker`
6. Now our jenkins user can execute the docker images.
7. To execute the container, run `docker exec -it jenkins bash`. And the container will open.
8. To verify that `docker.sock` is present inside the container, run `ls -ahl /var/run/docker.sock`.

## Updating docker image from jenkins

1. After updating, pull the image using `docker pull gujral1997/docker-nodejs-demo`.
2. Run the image using `docker run -p 3000:3000 -d --name my-nodjs-app gujral1997/docker-nodejs-demo`.
3. For confirmation, run `curl localhost:3000` which will prompt `Hello world` assuming everything is working.
