# Devops
This project provides example of using cloud development tools within azure.
### Docker Commands
some basic commands:
```
docker image
docker ps
docker run
docker rmi
```
push image to registry
>before pushing you should create repository on the dockerhub and replace {name}  by repository full name in commands bellow
```
docker tag {IMAGE ID} {name}
docker push {name}
```
