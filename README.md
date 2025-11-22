# Microservice Architecture Project

This project demonstrates a complete microservice architecture using Spring Boot and Spring Cloud. It consists of several independent services that communicate with each other to provide a billing system functionality.

## Application Overview
![Image](https://github.com/user-attachments/assets/7bb1d082-95ad-48f4-8c97-18ebf51199b7)
![Image](https://github.com/user-attachments/assets/730ca4f4-a9f5-4a48-80ea-0cd88028f020)

## 🏗 Architecture Overview

The system is built with the following core components:

*   **Service Discovery**: Netflix Eureka
*   **Configuration Management**: Spring Cloud Config
*   **API Gateway**: Spring Cloud Gateway
*   **Inter-service Communication**: OpenFeign
*   **Database**: H2 (In-memory)

### Services

| Service Name | Port | Description |
| :--- | :--- | :--- |
| **discovery-service** | `8761` | Eureka Server for service registration and discovery. |
| **config-service** | `9999` | Centralized configuration server backed by a Git repository. |
| **gateway-service** | `8888` | API Gateway acting as a single entry point, routing requests to appropriate services. |
| **customer-service** | `8081` | Manages customer data. |
| **inventory-service** | `8082` | Manages product inventory data. |
| **Billing-service** | `8083` | Manages bills and invoices, orchestrating data from Customer and Inventory services. |

## 🚀 Getting Started

### Prerequisites

*   **Java 21**
*   **Maven**

### Installation & Running

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd micro-service
    ```

2.  **Start the services in the following order:**

    It is crucial to start the infrastructure services first.

    1.  **Discovery Service**:
        ```bash
        cd discovery-service
        mvn spring-boot:run
        ```
    2.  **Config Service**:
        ```bash
        cd config-service
        mvn spring-boot:run
        ```
    3.  **Gateway Service**:
        ```bash
        cd gateway-service
        mvn spring-boot:run
        ```
    4.  **Customer Service**:
        ```bash
        cd customer-service
        mvn spring-boot:run
        ```
    5.  **Inventory Service**:
        ```bash
        cd inventory-service
        mvn spring-boot:run
        ```
    6.  **Billing Service**:
        ```bash
        cd Billing-service
        mvn spring-boot:run
        ```

## ⚙️ Configuration

The **Config Service** serves configuration files from a remote Git repository:
`https://github.com/Sami-khairy/micro-service-config-repo.git`

Each microservice fetches its configuration at startup.

## 🔌 Usage

Once all services are running, you can access the system through the **Gateway Service** at `http://localhost:8888`.

*   **Eureka Dashboard**: [http://localhost:8761](http://localhost:8761)
*   **Customer Service API**: `http://localhost:8888/CUSTOMER-SERVICE/customers`
*   **Inventory Service API**: `http://localhost:8888/INVENTORY-SERVICE/products`
*   **Billing Service API**: `http://localhost:8888/BILLING-SERVICE/bills`

*(Note: Service names in URLs might be case-sensitive depending on Eureka registration, usually uppercase by default in some configurations, or lowercase if configured).*

## 🛠 Technologies Used

*   **Spring Boot** (v3.5.7)
*   **Spring Cloud** (v2025.0.0)
*   **Spring Cloud Netflix Eureka**
*   **Spring Cloud Config**
*   **Spring Cloud Gateway**
*   **Spring Cloud OpenFeign**
*   **Spring Data JPA / REST**
*   **H2 Database**
*   **Lombok**
