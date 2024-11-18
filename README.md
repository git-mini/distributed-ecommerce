# eCom Microservices

This repository contains the implementation of an e-commerce platform using microservices architecture. The application uses Spring Boot, Spring Cloud Gateway, Kafka, and Feign Clients to provide a scalable and modular platform for managing products, orders, inventory, and notifications.

## Features

- **Product Service**: Handles product creation and retrieval.
- **Order Service**: Manages order placement and communicates with the Inventory service to verify product stock.
- **Inventory Service**: Provides real-time inventory checks for products.
- **Notification Service**: Sends order confirmation emails upon successful order placement.
- **API Gateway**: Routes API requests to the appropriate services and includes circuit breaker functionality.

## Architecture Overview

![Screenshot 2024-11-18 114143](https://github.com/user-attachments/assets/d18205f7-d5ad-46ca-8f2d-d9a9803218b5)


The application is split into the following services:

1. **Product Service** - Manages product information.
2. **Order Service** - Handles order placement and interacts with the Inventory Service.
3. **Inventory Service** - Keeps track of available stock and checks for product availability.
4. **Notification Service** - Listens for events related to order placements and sends confirmation emails.
5. **API Gateway** - Acts as a proxy to route requests and apply circuit breakers.

Additionally, the services communicate with each other using:

- **Kafka** for asynchronous messaging (order placement events).
- **Feign Clients** for synchronous communication between services (e.g., checking stock).

## Technologies Used

- **Spring Boot** for building the microservices.
- **Spring Cloud Gateway** for routing requests.
- **Kafka** for event-driven architecture.
- **Feign Client** for service-to-service communication.
- **Spring Data JPA** for persistence.
- **Spring Mail** for sending emails.

## Setup & Installation

### Prerequisites

- Java 17 (or later)
- Maven
- Docker (optional for other setups)

### Clone the repository

```bash
git clone https://github.com/your-username/eCom.git
cd eCom
```

### Running the services

1. **Start the API Gateway**:
    - The API Gateway handles routing and circuit breaker functionality for other services.
    - It forwards requests to the respective services based on the routes defined.
    - The API Gateway will run on `http://localhost:9000`.

2. **Start the individual services**:
    Each service can be run individually, for example:
    - **Product Service** on `http://localhost:8080`
    - **Order Service** on `http://localhost:8081`
    - **Inventory Service** on `http://localhost:8082`
    - **Notification Service** runs in the background as a Kafka listener.

You can start the services by running each service’s main application class (e.g., `ProductServiceApplication.java`, `OrderServiceApplication.java`, etc.).

Alternatively, if you have a `docker-compose.yml` setup, you can use Docker Compose to start all services at once.

```bash
docker-compose up
```
