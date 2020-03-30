# Udagram Microservices : Udacity Nano degree project
Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.


Links to Docker-hub images: 
  - Feed: https://hub.docker.com/repository/docker/khaleeed/udacity-restapi-feed
  - User: https://hub.docker.com/repository/docker/khaleeed/udacity-restapi-user 
  - Frontend: https://hub.docker.com/repository/docker/khaleeed/udacity-frontend 
  - ReverseProxy: https://hub.docker.com/repository/docker/khaleeed/reverseproxy


Instructions: 
  - Build the images: 
      - docker-compose -f docker-compose-build.yaml build --parallel 

  - Push the images: 
      - docker-compose -f docker-compose-build.yaml push

  - Run the containers:
      - docker-compose up
    
  - Create the infrastructure (kubernetes cluster) using the AWS management console,I used this article to create it(https://medium.com/faun/create-your-first-application-on-aws-eks-kubernetes-cluster-874ee9681293)

  - Apply confiMap and secrets: 
    - kubectl apply -f env-configmap.yaml
    - kubectl apply -f aws-secret.yaml
    - kubectl apply -f env-secret.yaml 

  - Apply Kubernetes deployments:
    - kubectl apply -f backend-feed-deployment.yaml 
    - kubectl apply -f backend-user-deployment.yaml
    - kubectl apply -f frontend-deployment.yaml
    - kubectl apply -f reverseproxy-deployment.yaml

  - Apply Kubernetes services:
    - kubectl apply -f backend-feed-service.yaml 
    - kubectl apply -f backend-user-service.yaml
    - kubectl apply -f frontend-service.yaml
    - kubectl apply -f reverseproxy-service.yaml
  
  - Apply port forwaring:
    - kubectl port-forward service/reverseproxy 8080:8080
    