
# Devops
This project provides example of using cloud development tools within azure.
### Docker Commands
some basic commands:
```
docker image
docker ps
docker run
docker rmi
docker logs -f {container name}
docker exec -it {conQtainer name} /bin/bash
docker stop $(docker ps -aq) -- stop all container
docker rm $(docker ps -aq) -- remove all container
docker rmi $(docker images -aq) # remove all images
docker system prune  -- all stopped containers  
					 -- all networks not used by at least one container  
					 -- all dangling images  
					-- all dangling build cache
docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d -- orchestration
```
push image to registry
>before pushing you should create repository on the dockerhub and replace {name}  by repository full name in commands bellow
```
docker tag {IMAGE ID} {name}
docker push {name}
```
### Kubectl Commands

    kubectl cluster-info
    kubectl get all -- pods, services, deployments..

### Deploy to Kubernetes 
there are two way to deploy to kubernetes. Declarative & Imperative.
#### Imperative
    kubectl run [container_name] --image=[image_name]
    kubectl port-forward [pod] [ports]

    kubectl create [resource]
    kubectl apply [resource] -- create or modify resources

	kubectl delete deployment [resource]

#### Declarative
	kubectl apply -f {filename.yaml}
	kubectl get deployment [resource] -o yaml #get yaml file from deployment
##### Debugging Pods
	kubectl logs [pod_name]
	kubectl describe pod [pod_name]
	kubectl exec [pod_name] -it sh
	kubectl get pod --watch
	kubectl get pod -o wide

#### Dashboard
[kubernetes dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/ "kubernetes dashboard")
### CI/CD
automate build image using github and dockerhub repositories.
>1. you should go to the builds tab on the dockerhub repository and chose link to github option
>2. chose 'connect' next to the github and authorize Docker Hub Builder
>3. you will be redirected on the account. go to the docker image repository -> builds -> github and select relevant repository from github
>4. you need to change docker file location according to your project. in this case it would be Shopping/Shopping.Client/Dockerfile 
> 5. Save
> 
> after that every push on the master branch will trigger docker hub builder and build newest version of the image


connect to the azure app service
> 1. Create azure app service:
>    - Create resource > Containers > Web App for Containers
>    - Chose your plan and go to the docker tab
>    - Chose single container option 
>    - chose docker hub and indicate your image name
>    -create resource and go to the resource
>  2. Go to deployment center
>  3. Check 'Continuous deployment' on and save
>  4. Copy webhook URL
>  5. Go to docker hub repository, webhooks tab paste url and create new webhook with any name.
