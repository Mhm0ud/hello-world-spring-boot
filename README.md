Hello World sample shows how to deploy [SpringBoot](http://projects.spring.io/spring-boot/) Hello World application with [Docker](https://www.docker.com/), Kubernetes, CI/CD using Github Actions.

## Prerequisite 

Installed:   
[Docker](https://www.docker.com/)   
[git](https://www.digitalocean.com/community/tutorials/how-to-contribute-to-open-source-getting-started-with-git)   


## Steps

##### Clone source code from git
```
$  git clone https://github.com/mhm0ud/hello-world-spring-boot .
```

##### Build Docker image
```
$ docker build -t="hello-world" .
```
Maven build will be executes during creation of the docker image.

>Note:if you run this command for first time it will take some time in order to download base image from [DockerHub](https://hub.docker.com/)

##### Run Docker Container
```
$ docker run -p 8080:8080 -d 
```

##### Test application

```
$ curl localhost:8080
```

the respone should be:
```
Hello Mahmoud!
```

##  Stop Docker Container:
```
docker stop `docker container ls | grep "hello-world:*" | awk '{ print $1 }'`
```

##  Kubernetes files:
Under deploy folder, we have two files that will deploy service, deployment, certificate, and ingress to a cluster

##  CI/CD: 
Maybe it's the time to use a new technology instead of Jenkins ;)
We are using GitHub Actions for the CI/CD, you can see the files under .github/workflows
The first step:
1. when push a new commit to the master branch, the CI will triggered and build a new image of the application and publish it to DockerHub.
2. when the first step finish, the deployment process will start with the new image that builded in the previous step.
