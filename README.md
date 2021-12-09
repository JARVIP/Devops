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
### CI
automate build image using github and dockerhub repositories.
>1. you should go to the builds tab on the dockerhub repository and chose link to github option
>2. chose 'connect' next to the github and authorize Docker Hub Builder
>3. you will be redirected on the account. go to the docker image repository -> builds -> github and select relevant repository from github
>4. you need to change docker file location according to your project. in this case it would be Shopping/Shopping.Client/Dockerfile 
> 5. Save
> 
> after that every push on the master branch will trigger docker hub builder and build newest version of the image
