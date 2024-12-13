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


## Table of Microservice Repositories
| **Service**         | **Repository Link**                       |
|---------------------|-------------------------------------------| 
| `store-front` | [store-front-L8](https://github.com/BenYee15/store-front-L8) |
| `store-admin` | [store-admin-L8](https://github.com/BenYee15/store-admin-L8) |
| `order-service` | [order-service-L8](https://github.com/BenYee15/order-service-L8) |
| `product-service` | [product-service-L8](https://github.com/BenYee15/product-service-L8) |
| `makeline-service` | [makeline-service-L8](https://github.com/BenYee15/makeline-service-L8) |
| `ai-service` | [ai-service-L8](https://github.com/BenYee15/ai-service-L8) |
| `mongodb` | [mongodb](https://github.com/docker-library/mongo) |

## Docker Images

## Deployment Files 
