# 🏥 Patient Management System

A **production-ready healthcare management system** built with **Spring Boot Microservices, React, and modern DevOps tools**.  
The system manages patients, billing, authentication, and analytics with scalable and secure architecture.

## 🚀 Features
- **Patient Service**: Create, update, delete, and manage patient records.
- **Billing Service**: gRPC-based service to handle billing requests.
- **Analytics Service**: Kafka consumer for processing and analyzing patient events.
- **Authentication Service**: JWT-based authentication and authorization.
- **API Gateway**: Centralized routing, load balancing, and security.
- **OpenAPI Docs**: Interactive documentation for all services.

## 🏗️ Architecture
- **Spring Boot Microservices** (Patient, Billing, Analytics, Auth, API Gateway).
- **gRPC** communication between microservices.
- **Apache Kafka** for event-driven architecture.
- **Docker & Docker Compose** for containerization and orchestration.
- **PostgreSQL**
- **Spring Security + JWT** for authentication & authorization.

## 🛠️ Tech Stack
- **Backend**: Java, Spring Boot, Spring Security, Spring Data JPA, gRPC, Kafka  
- **Database**: PostgreSQL  
- **DevOps**: Docker, Docker Compose
- **Others**: OpenAPI/Swagger, API Gateway  

## 📂 Services
- `patient-service`: Manage patients, integrates with billing & analytics.
- `billing-service`: Handle billing requests via gRPC.
- `analytics-service`: Consume Kafka events for insights.
- `auth-service`: Handle login, token validation, JWT.
- `api-gateway`: Centralized entry point for client apps.
## 🔄 System Architecture Flow

<img width="1651" height="555" alt="image" src="https://github.com/user-attachments/assets/992e69cd-985e-4bd3-aced-766ad253766a" />


The **Patient Management System** is designed with a microservices architecture, where each service is responsible for a specific domain (patients, billing, authentication, analytics). The flow of data across the system is as follows:

### 1. Client (Frontend)
- Users (e.g., doctors, staff) interact with the system through a web client.  
- Example requests:  
  - `GET http://localhost:4000/api/patients` → fetch patient list.  
  - `POST http://localhost:4000/api/patients` → create a new patient.  

### 2. API Gateway
- All client requests first go through the **API Gateway**.  
- Responsibilities:  
  - **Routing**: forward the request to the correct microservice.  
  - **Authentication**: validate the JWT token with the **Auth Service**.  
  - **Authorization**: allow or block access based on token validity.  

### 3. Auth Service
- Provides login (`/auth/login`) and issues **JWT tokens**.  
- Validates tokens for incoming requests via the API Gateway.  

### 4. Patient Service
- Main microservice handling **CRUD operations** for patient data.  
- Stores data in **PostgreSQL**.  
- On specific actions (e.g., patient creation):  
  - Publishes an event to **Kafka** (for asynchronous processing).  
  - Calls **Billing Service via gRPC** to create or update billing information.  

### 5. Billing Service
- Exposes a **gRPC server** to receive requests from Patient Service.  
- Handles all billing-related logic (e.g., generating invoices, storing cost data).  

### 6. Kafka (Event Streaming)
- Enables asynchronous communication between microservices.  
- **Patient Service** acts as a **Producer**, publishing events (e.g., `PatientCreated`).  
- **Analytics Service** acts as a **Consumer**, processing patient-related events.  

### 7. Analytics Service
- Consumes events from Kafka for real-time analytics (e.g., number of patients created).  
- Exposes APIs (`/api/analytics`) that the client can access via the API Gateway.  

### 8. Database (PostgreSQL)
- Stores persistent patient data and related entities.  
- Only **Patient Service** communicates directly with the database (service owns its data).  


