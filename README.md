# Udagram Microservices : Udacity Nano degree project
Links to Docker-hub images: 
  - Feed: https://hub.docker.com/repository/docker/habiballaah/udacity-restapi-feed
  - User: https://hub.docker.com/repository/docker/habiballaah/udacity-restapi-user 
  - Frontend: https://hub.docker.com/repository/docker/habiballaah/udacity-frontend 
  - ReverseProxy: https://hub.docker.com/repository/docker/habiballaah/reverseproxy

Screenshots are located in the root of the repository.

Instructions: 
  - Build the images: 
      - docker-compose -f docker-compose-build.yaml build --parallel 

  - Push the images: 
      - docker-compose -f docker-compose-build.yaml push

  - Run the containers:
      - docker-compose up
    
  - Create the infrastructure (kubernetes cluster) using the AWS management console,I used this article to create it:https://eksctl.io/usage-creating-and-managing-clusters/: 

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
    
    
