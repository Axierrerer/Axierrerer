<h1 align="center">Python Backend Developer</h1>
<h3 align="center">Hi, I'm Evgeny 👋</h3>
<p align="center">B2B systems · Event-driven architecture · Integrations · Performance</p>

<p align="center">
  <a href="https://t.me/Axierrere"><img src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"/></a>
  <a href="mailto:antonovevgenii71@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
  <a href="https://www.linkedin.com/in/evgenii-antonov-83763343a/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
</p>

---

## About me

Python backend developer with **4+ years** of experience building B2B systems: e-commerce platforms and procurement/supply automation for the aviation industry.

I build Django applications, REST APIs with DRF and standalone FastAPI services, and I work end to end: from requirements and API design to testing, release and production support.

📍 Based in Georgia (UTC+4) · 🌍 Open to remote Python backend roles

---

## ⚡ Selected results

- 🚀 Made a business-critical API **10x+ faster** (8–12 s → 400–800 ms) by rewriting SQL, eliminating N+1 queries and adding indexes with zero downtime
- 🏗️ Designed and shipped **5 production services** from scratch, covering architecture, Docker, GitLab CI/CD and deployment to all environments
- 📉 Cut main application **CPU load by ~30%** by extracting document generation into a dedicated service
- 🔁 Built service-to-service integration on **Temporal** workflows with idempotent processing, plus a FastAPI service with Elasticsearch search
- 🚦 Built a **Redis-based sliding window rate limiter** (sorted sets, MULTI/EXEC) enforcing limits consistently across multiple service instances
- 📄 Automated Excel/PDF generation of business documents, fully replacing manual work by managers; later refactored its **20K+ line** codebase, verified with golden-file comparison

---

## 🧩 Key projects

> Commercial projects are under NDA, so their code is private. Here is what I worked on.

### ✈️ ERP for an aviation parts company
Internal ERP covering orders, parts accounting, warehouses, commercial offers, invoices and pricing.
`Django` `DRF` `PostgreSQL` `Celery` `Redis` `Docker` `GitLab CI/CD`

### 📄 Document generation service
Event-driven service that consumes Kafka events and generates Excel and PDF business documents from per-supplier templates, integrated with two external systems. Extracted from the main app (−30% CPU) and later refactored with golden-file regression testing.
`Python` `Kafka` `openpyxl` `Docker`

### 🔁 Analytics platform: S2S integration
Temporal orchestrator (a workflow per business task, idempotent processing, Telegram notifications to managers) plus a FastAPI service reading analytics data, with Elasticsearch search indexed via Celery Beat.
`Temporal` `FastAPI` `PostgreSQL` `Elasticsearch` `Celery`

### 🔎 Reusable Elasticsearch events library
Internal Python library with overridable repositories for Pydantic models, built for reuse across services, with zero-downtime index changes.
`Python` `Pydantic` `Elasticsearch`

### 🛒 B2B e-commerce platform
REST API with payment and logistics integrations, background processing and caching.
`DRF` `Celery` `RabbitMQ` `Redis` `PostgreSQL`

---

## 🛠️ Open-source / pet projects

### [Event-Driven Orders Processing Platform](https://github.com/Axierrerer/REPO-NAME)
Order processing platform for a small e-commerce store: product catalog, users and roles, checkout, inventory management and notifications.
- **Microservices** on Python (FastAPI, asyncio), each owning its own domain
- **Async + sync communication** — events via Kafka, direct calls via REST and gRPC
- **Choreography-based saga** — an order goes from checkout to delivery with each service reacting to other services' events; on failure, services publish compensating events to roll back their steps

`FastAPI` `asyncio` `Kafka` `gRPC` `PostgreSQL` `Docker`

### [Async Payment Processing Service](https://github.com/Axierrerer/REPO-NAME)
Payment-provider-style microservice: accepts payments via a REST API (`202 Accepted`), processes them asynchronously through an emulated payment gateway and notifies merchants via signed webhooks.
- **Transactional Outbox** — payment and event are written in one transaction; a separate relay publishes events with publisher confirms and `mandatory` routing, so no event is lost or silently dropped
- **Idempotency** — `Idempotency-Key` header plus request hash protects against duplicate payments; idempotent consumer for at-least-once delivery
- **Retries & DLQ** — exponential backoff via per-delay TTL retry queues (2s → 4s → 8s), Dead Letter Queue for messages that failed all attempts
- **Clean layering** — domain entities with business invariants, use cases, Unit of Work, repositories

`FastAPI` `Pydantic v2` `SQLAlchemy 2.0 (async)` `PostgreSQL` `RabbitMQ` `FastStream` `Alembic` `Docker`

---

## 🧰 Tech stack

**Languages & frameworks**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-A30000?style=flat-square&logo=django&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy_2.0-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)

**Data & messaging**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=flat-square&logo=celery&logoColor=white)
![Temporal](https://img.shields.io/badge/Temporal-000000?style=flat-square&logo=temporal&logoColor=white)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=flat-square&logo=minio&logoColor=white)

**DevOps & observability**
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab_CI/CD-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F46800?style=flat-square&logo=grafana&logoColor=white)
![OpenAPI](https://img.shields.io/badge/OpenAPI-6BA539?style=flat-square&logo=openapiinitiative&logoColor=white)
