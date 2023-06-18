# nx-azure-microservice-with-nginx-ingress by arbrsts

This project offers a robust solution for developing and deploying microservices using the NX tool. It simplifies the development process, ensures scalability, and facilitates deployment on Azure Kubernetes Service (AKS) with Nginx Ingress. With this solution, you can effectively manage and orchestrate your microservices architecture while leveraging the capabilities of Azure's cloud platform.

## Key Features

- **NX for Microservices:** Benefit from efficient management and organization of multiple microservices using the NX tool. It streamlines code generation, enforces architectural constraints, and facilitates dependency management, resulting in a scalable and maintainable microservices architecture.

- **Azure Kubernetes Service (AKS):** Deploy your microservices with confidence on AKS, which provides a reliable and scalable infrastructure powered by Azure's cloud platform. AKS offers container orchestration, automatic scaling, and simplified management of your microservices.

- **Nginx Ingress:** Easily deploy Nginx Ingress using the provided scripts. Nginx Ingress acts as a versatile reverse proxy and load balancer, enabling efficient routing and traffic management for your microservices within the AKS cluster.

- **Next.js Microfrontends**: Develop and deploy multiple Next.js microfrontends as part of your microservices architecture. Leverage the power of Next.js to build interactive and performant user interfaces for your microservices. The project provides an organized structure to manage and deploy these microfrontends efficiently.

## Project structure
```
├── apps/
│   ├── app/                       # Directory for the "app" microservice.
│   └── marketing/                 # Directory for the "marketing" microservice.
├── azure.pipelines.yml            # Configuration file for Azure Pipelines, enabling CI/CD workflows.
├── conf/nginx.conf                # Configuration file for Nginx, specifying the server settings and routing rules.
├── docker-compose.yml             # Docker Compose file for local development, defining the services and their dependencies.
├── ingress.yaml                   # YAML file defining the Kubernetes Ingress resource for routing external traffic to the microservices.
├── kubernetes.yaml                # YAML file containing the Kubernetes resource configurations for deploying the microservices.
├── nx.json                        # Configuration file for the NX workspace, specifying the project commands and dependencies.
└── packages/                      # Directory containing any additional packages or shared code used in the project.
```
## Deployment

### Local

To deploy the project locally, follow these steps:

1. Start nginx to route requests properly: `docker compose up`
2. Install the dependencies: `npm install`
3. Start all services, including the two front-end microservices on `localhost:3000` (app) and `localhost:3001` (marketing): `npm run dev`
4. Visit `localhost:3000` to access the `app` service, and `localhost:3001` to access the `marketing` service.

### Azure

To deploy the project on Azure AKS, follow these steps:

1. Create the AKS cluster using Azure CLI or the portal. Refer to the [official documentation](https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-portal?tabs=azure-cli) for detailed instructions.
2. Register Azure Container Registry with the container. Follow the steps provided in the [official documentation](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration?tabs=azure-cli).
3. Build and push the Docker images for the `app` and `marketing` Next.js images to Azure Container Registry (ACR).
4. Apply the image and resource configuration using the following command: `kubectl apply -f ingress.yaml kubernetes.yml`
5. Retrieve the external IP address of the ingress service by running: `kubectl get service`. Visit the provided IP address to access the webpage.

That's it! You've deployed the project locally or on Azure AKS with Nginx Ingress.
