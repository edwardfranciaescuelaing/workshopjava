# Spring Docker Primer Web Application

This project is a small web application built with Spring Boot and Docker. It involves creating a simple RESTful service, containerizing the application with Docker, and deploying it both locally and on an AWS EC2 instance using Docker. The application is built using Maven and is compatible with Java 17.

## Table of Contents
1. [Architecture](#architecture)
2. [Setup Process](#setup-process)
3. [Build and Run Docker Image](#build-and-run-docker-image)
4. [Docker Hub Deployment](#docker-hub-deployment)
5. [AWS Deployment](#aws-deployment)
6. [Testing and Logs](#testing-and-logs)
7. [Screenshots](#screenshots)

---

## Architecture

The application is composed of:
- **Spring Boot** as the web framework for RESTful APIs.
- **Docker** to package the Spring application into a container and allow it to run consistently across environments.
- **AWS EC2** as the deployment environment.

Key components:
- **Spring Boot** application with a simple REST controller that returns a greeting.
- **Docker** container that holds the compiled Java classes and dependencies.
- **Docker Compose** to run the application alongside a MongoDB service.

### Application Flow

1. The user accesses the `/greeting` endpoint on the Spring Boot application.
2. The application responds with a customized greeting based on the request.
3. Docker packages the application, which is deployed either locally or on AWS.

---

## Setup Process

### Prerequisites

Ensure you have the following tools installed:
- Java 17 or higher
- Maven
- Docker
- AWS CLI (for AWS deployment)
- Docker Compose

### 1. Clone the Repository

```bash
git clone [https://github.com/yourusername/spring-docker-primer](https://github.com/edwardfranciaescuelaing/workshopjav)
cd spring-docker-primer
