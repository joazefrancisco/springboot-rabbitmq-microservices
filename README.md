# RabbitMQ Microservices with Spring Boot

This project demonstrates a **microservices architecture using Spring Boot and RabbitMQ**, focusing on **asynchronous communication, decoupling, and event-driven design**.

---

## Overview

This system is composed of two microservices that communicate through RabbitMQ:

- A **Producer Service** that publishes messages (events)
- A **Consumer Service** that listens and processes messages asynchronously

Instead of direct HTTP communication, services exchange messages via a message broker, improving scalability and resilience.

---

## Technologies

- Java 17+
- Spring Boot
- Spring AMQP
- RabbitMQ
- Maven
- Docker (for RabbitMQ)

---

## Architecture

The system follows an **Event-Driven Architecture (EDA)**:

### Producer Service
- Creates and sends messages
- Publishes events to RabbitMQ
- Uses `RabbitTemplate` to send data

### Consumer Service
- Listens to RabbitMQ queues using `@RabbitListener`
- Processes incoming messages asynchronously
- Decoupled from the producer

### RabbitMQ Broker
- Handles message routing
- Stores messages in queues
- Ensures asynchronous delivery

---

## Message Flow

1. Producer creates an event (message)
2. Message is sent to RabbitMQ exchange
3. RabbitMQ routes it to the correct queue
4. Consumer receives and processes the message

---

## How to Run the Project

### 1. Start RabbitMQ (Docker)

Run RabbitMQ with management UI:

```bash
docker run -d --name rabbitmq \
-p 5672:5672 \
-p 15672:15672 \
rabbitmq:3-management
