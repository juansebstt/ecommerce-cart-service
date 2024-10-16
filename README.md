# E-commerce Cart Service

## Overview

The **E-commerce Cart Service** is responsible for managing the shopping cart functionality for the e-commerce platform. It allows users to add, remove, and update products in their shopping carts. This service interacts with other microservices like the **E-commerce Catalog Service** to retrieve product details and the **E-commerce Order Service** when placing orders.

## Features

- **Cart Management**: Add, update, and remove items from the cart.
- **Product Validation**: Communicates with the **Catalog Service** to validate product availability and details.
- **Inter-Service Communication**: Shares cart information with the **Order Service** when placing an order.

## Technologies Used

- **Java**
- **Spring Boot**
- **Maven** (for dependency management)
- **PostgreSQL** (for cart data storage)

## Prerequisites

Before running this service, ensure you have the following:

- **Java JDK 11 or higher**
- **Maven** (for building the project)
- A running **PostgreSQL** database (or other supported database).
- Access to the relevant microservices (e.g., Catalog Service, Order Service).

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/juansebstt/ecommerce-cart-service.git
    ```

2. Navigate to the project directory:

    ```bash
    cd ecommerce-cart-service
    ```

3. Build the project using Maven:

    ```bash
    mvn clean instal
    ```


## Configuration

You need to configure the database and application settings in your `application.yml` or `application.properties` file.

### Sample Configuration

```yaml
server:
  port: 8084

spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/ecommerce_cart_db
    username: yourUsername
    password: yourPassword
    driver-class-name: org.postgresql.Driver

  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

  application:
    name: ecommerce-cart-service
```

## Inter-Service Communication

The **E-commerce Cart Service** interacts with the following microservices:

- **[E-commerce Catalog Service](https://github.com/juansebstt/ecommerce-catalog-service)**:
    - Retrieves product details to validate items being added to the cart.
- **[E-commerce Order Service](https://github.com/juansebstt/ecommerce-order-service)**:
    - Sends cart information when an order is placed.
- **[E-commerce User Service](https://github.com/juansebstt/ecommerce-user-service)**:
    - Manages user-specific cart information.
- **[E-commerce API Gateway](https://github.com/juansebstt/ecommerce-api-gateway)**
    - Routes cart-related requests from the frontend.

## Usage

### Adding an Item to the Cart

To add an item to the cart, make a POST request to the `/cart/add` endpoint with the following payload:

```json
{
  "productId": "12345",
  "quantity": 2,
  "userId": "user-001"
}
```

### Removing an Item from the Cart

To remove an item from the cart, make a DELETE request to the `/cart/remove` endpoint with the following payload:

```json
{
  "productId": "12345",
  "userId": "user-001"
}
```

## Testing

You can use tools like **Postman** to test the various API endpoints. Ensure proper authentication if the service is secured.

## Contributing

Feel free to submit pull requests or open issues if you find bugs or want to contribute to the project.