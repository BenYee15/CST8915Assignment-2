# Cloud-Native App for Best Buy

## Updated Application Architecure
![Application Architecture](https://github.com/user-attachments/assets/ca090f66-4268-470e-898d-4b3b17f1ca39)


## Application and Architecture Explanation
The API acts as the entry point and splits between the store-front(customers) and store-admin(employees).
The store-front sends request to the order-service and product-service, while the store-admin communicates with the makeline-service.
The order-service send the order to order queue (RabbitMQ).
The product-service provides the products details to the store-front.
The makeline-service consumes the data from the order queue and updates the MongoDB.
MongoDB is a shared central database storing all orders and data of the products. It also in contained in a pod with persistent volume to ensure data is retained if the pod is recreated.
The ai-service is used to create a better user experience by recommending products and generating images for products.

## Deployment Instructions
In order to do this, A Kubernetes cluster must be running on Azure, the Kubernetes cmd tool installed and configured, and Docker for the containerizing microservices. 

Each service also needs a Dockerfile and Docker image.
Repeat the following command for each service:
```
docker build -t store-front:latest 
```

From there, push the images to a container registry (Docker Hub).
Repeat the following command for each service:
```
docker push store-front:latest
```

A YAML file is needed to define resources for each service. If I could've continued working on the assignment, I would've created a seperate YAML file for each service, and I would've changed value of image under containers to point to its docker registry. I would've also created a new YAML file for the ingress (NGINX) pod.
The file can be located here: https://github.com/BenYee15/CST8915Assignment-2/blob/main/Deployment%20Files/aps-all-in-one.yaml


After the YAML files are prepared, they can be applied to the clusters using the command:
```
kubectl apply -f store-front.yaml
kubectl apply -f store-admin.yaml
kubectl apply -f order-service.yaml
kubectl apply -f makeline-service.yaml
kubectl apply -f product-service.yaml
kubectl apply -f ai-service.yaml
kubectl apply -f rabbitmq.yaml
kubectl apply -f mongodb.yaml
kubectl apply -f ingress.yaml
```

Verification of the deployments and Services can be checked using the following commands:
```
kubectl get deployments
kubectl get pods
kubectl get services
```

In order to obtain the specific IP or domain used to access the application, use the following command:
```
kubectl get ingress
```

## Table of Microservice Repositories
| **Service**         | **Repository Link**                       |
|---------------------|-------------------------------------------| 
| `store-front` | [store-front](https://github.com/BenYee15/store-front-L8) |
| `store-admin` | [store-admin](https://github.com/BenYee15/store-admin-L8) |
| `order-service` | [order-service](https://github.com/BenYee15/order-service-L8) |
| `product-service` | [product-service](https://github.com/BenYee15/product-service-L8) |
| `makeline-service` | [makeline-service](https://github.com/BenYee15/makeline-service-L8) |
| `ai-service` | [ai-service](https://github.com/BenYee15/ai-service-L8) |
| `mongodb` | [mongodb](https://github.com/docker-library/mongo) |

## Docker Images

## Deployment Files 
