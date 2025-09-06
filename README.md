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

