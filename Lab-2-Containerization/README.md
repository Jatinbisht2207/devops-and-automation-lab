# Lab 2: Containerization and Kubernetes Orchestration

## 1. Objective

To understand containerization using Docker, manage containers and images, implement persistent storage, configure Docker networking, deploy applications using Kubernetes, and automate deployment using Jenkins CI/CD.

## 2. Technologies Used

- Docker
- Docker Compose
- Docker Hub
- Kubernetes
- Minikube
- kubectl
- Jenkins
- Git and GitHub
- Python
- Flask
- Redis
- Ubuntu on WSL2

## 3. Application Overview

A simple Flask web application was developed and containerized using Docker.

Application URL: /
Application Port: 5000

The application was packaged into a Docker image and deployed to a Kubernetes cluster using a Deployment and NodePort Service.

## 4. Docker Implementation

### Q1: Containerization

- Created a Dockerfile using Python 3.11 slim as the base image.
- Installed Flask dependencies.
- Built the Docker image.
- Created and executed a Docker container.
- Inspected Docker image layers and container details.

### Q2: Docker Management and Compose

- Listed, started and stopped containers.
- Inspected and tagged Docker images.
- Pushed the application image to Docker Hub.
- Created a Docker Compose configuration with Flask and Redis services.

Docker Hub Image:
jatinbisht22/lab2-flask-app

### Q3: Docker Storage

Three storage behaviors were demonstrated:

1. Container writable layer: Data was lost after container deletion.
2. Named volume: Data persisted after container deletion.
3. Bind mount: Host files and container files were synchronized.

Named Volume:
lab2-data

### Q4: Docker Networking

- Created a custom Docker network named lab2-network.
- Started an Nginx container.
- Tested communication using the container name.
- Retrieved the container IP address.
- Verified communication using the container IP.

## 5. Kubernetes Implementation

### Q5: Deployment and Service

- Installed Minikube and kubectl.
- Started a local Kubernetes cluster using Docker driver.
- Created Kubernetes Deployment and Service manifests.
- Deployed the Flask application.
- Verified running Pods and Services.

Deployment:
lab2-flask-deployment

Service:
lab2-flask-service

Service Type:
NodePort

NodePort:
30007

Initial replicas:
2

### Q6: Scaling and Deployment Strategies

The following deployment operations were performed:

1. Scaled the application from 2 to 4 replicas.
2. Performed a rolling update from image v1 to v2.
3. Verified the updated deployment.
4. Executed a rollback to image v1.
5. Scaled the deployment back to 2 replicas.

Final deployment status:
2/2 replicas available.

## 6. Jenkins CI/CD Integration

### Q7: Continuous Deployment

The existing Jenkins pipeline from Lab 1 was extended to support Kubernetes deployment.

Pipeline stages:

1. Checkout SCM
2. Build
3. Test
4. Deploy to Kubernetes
5. Verify Deployment
6. Post Actions

Jenkins was configured to access Minikube using a dedicated Kubernetes configuration file.

The pipeline automatically applies Kubernetes manifests using:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

Deployment status is verified using:

kubectl rollout status deployment/lab2-flask-deployment

Jenkins Build #9 completed successfully in 23 seconds.

## 7. Final Verification

The following commands were used:

kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get services

Final observations:

- Minikube node status: Ready
- Deployment replicas: 2/2
- Running Pods: 2
- Kubernetes Service: NodePort
- Jenkins pipeline: Successful

## 8. Conclusion

The practical successfully demonstrated Docker containerization, image management, persistent storage, container networking, Kubernetes orchestration, scaling, rolling updates, rollbacks, and Jenkins-based continuous deployment.

The integration of Jenkins with Kubernetes automated the application deployment process and verified the successful running state of the application.
