# Updated Application Architecure
![Application Architecture](https://github.com/user-attachments/assets/aa376665-c3d6-418b-b73f-1d017990ec2b)
# Application and Architecture Explanation
The API acts as the entry point and splits between the store-front(customers) and store-admin(employees).
The store-front sends request to the order-service and product-service, while the store-admin communicates with the makeline-service.


# Deployment Instructions
# Table of Microservice Repositories
| **Service**         | **Repository Link**                       |
|---------------------|-------------------------------------------| 
| `store-front` | [store-front-L8](https://github.com/BenYee15/store-front-L8) |
| `store-admin` | [store-admin-L8](https://github.com/BenYee15/store-admin-L8) |
| `order-service` | [order-service-L8](https://github.com/BenYee15/order-service-L8) |
| `product-service` | [product-service-L8](https://github.com/BenYee15/product-service-L8) |
| `makeline-service` | [makeline-service-L8](https://github.com/BenYee15/makeline-service-L8) |
| `ai-service` | [ai-service-L8](https://github.com/BenYee15/ai-service-L8) |
| `mongodb` | [mongodb](https://github.com/docker-library/mongo) |
