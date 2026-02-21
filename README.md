# Cortex --- Stateful Memory Service for Intelligent Agents

Cortex is a distributed backend service designed to store and retrieve
session-aware memory for intelligent agents and real-time systems. It
enables AI agents to maintain conversation context across interactions
by providing scalable, persistent, and low-latency memory storage.

This project demonstrates backend infrastructure design using
event-driven architecture, asynchronous processing, and cloud-native
deployment practices.

------------------------------------------------------------------------

# Problem

Modern intelligent systems and AI agents are stateless by default.
Without persistent memory, agents cannot retain context between
interactions, leading to poor user experience and limited functionality.

Cortex solves this by providing:

-   Persistent session memory storage
-   Fast memory retrieval
-   Scalable asynchronous memory updates
-   Support for concurrent sessions

------------------------------------------------------------------------

# Architecture Overview

    Client
      ↓
    Spring Boot API Service
      ↓
    Kafka Event Stream
      ↓
    Memory Consumer Service
      ↓
    PostgreSQL Database

    Retrieval Flow:

    Client → API Service → PostgreSQL → Response

------------------------------------------------------------------------

# Key Features

-   Session-aware memory storage and retrieval
-   Event-driven architecture using Kafka
-   Scalable backend infrastructure using Spring Boot
-   Concurrent session support
-   Persistent storage using PostgreSQL
-   Containerized deployment using Docker
-   Optimized memory retrieval using indexed queries

------------------------------------------------------------------------

# Tech Stack

Backend
- Java 17
- Spring Boot

Database
- PostgreSQL

Event Streaming
- Apache Kafka

Infrastructure
- Docker

Architecture
- Event-driven microservices
- Distributed system design

------------------------------------------------------------------------

# Core Components

## API Service

Handles incoming memory requests.

Endpoints:

Store memory:

POST /memory

Retrieve memory:

GET /memory/{sessionId}

------------------------------------------------------------------------

## Memory Storage Service

Stores memory data in PostgreSQL using optimized schema and indexing.

Example schema:

memory_table

-   id
-   session_id
-   user_id
-   message
-   timestamp

------------------------------------------------------------------------

## Event Streaming (Kafka)

Kafka is used to asynchronously process memory updates.

Benefits:

-   Improves scalability
-   Prevents API blocking
-   Enables distributed processing
-   Supports high-throughput workloads

------------------------------------------------------------------------

## Database Layer

PostgreSQL provides persistent storage with indexed queries for fast
retrieval.

Indexes:

-   session_id
-   timestamp

------------------------------------------------------------------------

# Example Workflow

Store memory:

POST /memory

{ "sessionId": "123", "userId": "renil", "message": "My name is Renil" }

Flow:

1.  API receives request
2.  Kafka event is published
3.  Consumer stores memory in PostgreSQL

Retrieve memory:

GET /memory/123

Response:

\[ { "message": "My name is Renil", "timestamp": "2026-01-10T10:00:00"
}\]

------------------------------------------------------------------------

# Scalability Design

Cortex is designed to scale horizontally.

Supports:

-   Multiple API service instances
-   Multiple Kafka consumers
-   Concurrent session handling
-   Distributed deployment using containers

------------------------------------------------------------------------

# Project Structure

cortex-memory-service

-   api-service
-   memory-consumer
-   database
-   docker
-   README.md

------------------------------------------------------------------------

# Running the Project

Prerequisites:

-   Java 17
-   Docker
-   PostgreSQL
-   Kafka

Clone repository:

git clone https://github.com/yourusername/cortex-memory-service

Start services:

docker-compose up

Run Spring Boot service:

./mvnw spring-boot:run

------------------------------------------------------------------------

# Design Decisions

Event-driven architecture was chosen to:

-   Improve system scalability
-   Enable asynchronous processing
-   Reduce request latency
-   Support distributed workloads

PostgreSQL was chosen for reliable and indexed persistent storage.

Kafka was used to decouple memory ingestion from storage processing.

------------------------------------------------------------------------

# Future Improvements

-   Add Redis caching for faster retrieval
-   Add memory expiration policies
-   Deploy to Kubernetes
-   Add monitoring using Prometheus and Grafana

------------------------------------------------------------------------

# Use Cases

-   AI agent memory systems
-   Conversational AI platforms
-   Chat systems requiring persistent context
-   Distributed backend systems

------------------------------------------------------------------------

# Author

Renil Soni\
Software Engineer --- Distributed Systems & Backend Infrastructure
