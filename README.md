<h1 align="center">Python Backend Developer</h1>
<h3 align="center">Hi, I'm Evgeny 👋</h3>
<p align="center">Microservices · Event-driven architecture · Integrations · Performance</p>

<p align="center">
  <a href="https://t.me/Axierrere"><img src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"/></a>
  <a href="mailto:antonovevgenii71@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
  <a href="https://www.linkedin.com/in/evgenii-antonov-83763343a/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
</p>

---

## About me

Python backend developer with **5+ years** of commercial experience. I design and ship asynchronous microservices on FastAPI with event-driven communication (Kafka, RabbitMQ, Temporal) and develop a large ERP system built on Django REST Framework.

My focus is performance and reliability: I've made key APIs **10x+ faster**, optimized SQL queries from seconds down to milliseconds, and built resilient service-to-service integrations (Transactional Outbox, Inbox pattern, idempotency, retries, Circuit Breaker). I own my services end to end — from design and development to CI/CD, monitoring and production support — and work closely with analysts and product teams.

🌍 Open to remote Python backend roles

---

## ⚡ Selected results

- 🚀 Made key ERP APIs **10x+ faster** (8–12 s → 400–800 ms); the main SQL query went from **~8 s to ~50–60 ms** after rewriting correlated subqueries into CTEs with PostgreSQL window functions, fixing N+1 and adding indexes with zero downtime
- 🏗️ Designed and shipped **asynchronous microservices to production** (FastAPI, Kafka, Temporal), gradually extracting integration features from a Django monolith
- 📄 Extracted document generation into a separate service, cutting the monolith's **CPU load by ~30%**; the service is now used by a second development team
- ⚡ Made XLSX → PDF conversion **~12x faster** (4–5 s → 300–400 ms) by replacing a LibreOffice process per document with a persistent conversion server (unoserver)
- 💳 Built payment processing with **zero double charges**: signed webhooks, replay protection, idempotency keys and atomic balance updates
- 🔁 Implemented reliable event delivery with Transactional Outbox, Inbox pattern and correlation ID deduplication
- 🔍 Set up end-to-end tracing with a single trace ID across HTTP, Kafka and Temporal (Promtail, Loki, Grafana)

---

## 💼 Experience

### ✈️ Python Backend Developer — aviation parts company
*August 2024 — present*

Internal development team: a corporate B2B ERP system for aviation parts sales and procurement (Django REST Framework, PostgreSQL) and microservices for document processing, integrations and analytics (FastAPI, Kafka, Temporal, Elasticsearch).

> Commercial projects are under NDA, so their code is private. Here is what I worked on.

#### 📄 Document generation microservice
Extracted commercial offer and invoice generation from the monolith into an isolated service used by two development teams. Consumes Kafka events, generates XLSX/PDF documents from 20+ templates, stores files in S3 (MinIO) and publishes result events; the ERP is updated back through a Temporal workflow (eventual consistency). Idempotent processing via the Inbox pattern, extensible architecture built on Strategy, Factory and Template Method patterns.
`Python` `Kafka (confluent-kafka)` `Temporal` `PostgreSQL` `MinIO (S3)` `openpyxl` `unoserver` `Docker` `GitLab CI/CD`

#### 🔀 Integration gateway & email monitoring
A Temporal-based gateway between external automations and the ERP: durable workflows for creating and updating ERP data, declarative retries and a Redis cache for reference data, isolating automations from monolith changes. A FastAPI + Temporal service that monitors mailboxes via the Gmail API (OAuth2 with automatic token refresh, encrypted secrets) and stores incoming emails in S3 within 10 seconds of arrival.
`Temporal` `FastAPI` `Gmail API` `OAuth2` `Redis` `MinIO (S3)` `PostgreSQL`

#### 🔁 Analytics platform
Two services: a Temporal orchestrator for business processes (including idempotent Telegram notifications to managers via aiogram) and a FastAPI data access service on top of a replica of the main database. Moved company search and matching to Elasticsearch (analyzers, filters, relevance scoring) with zero-downtime reindexing via alias switching. JWT + API key auth, Redis sliding window rate limiter, request logging middleware, concurrency limits for service-to-service calls (httpx, asyncio.Semaphore).
`Temporal` `FastAPI` `Elasticsearch` `Redis` `PostgreSQL` `Celery Beat`

#### 🔎 Company data matching service
Verifies company data extracted from incoming emails. Two-stage search — exact match on B-tree indexes and fuzzy trigram search (pg_trgm, GIN, similarity) with weighted per-field scoring, ~100–200 ms response time. Company directory sync from the ERP database via Celery Beat with a Redis distributed lock.
`FastAPI` `async SQLAlchemy` `PostgreSQL` `pg_trgm` `Alembic` `Redis`

#### 🏢 ERP system
- Developed REST API and domain logic for the end-to-end process from customer request to procurement and delivery, working closely with analysts and the product team
- Performance audit (django-silk, EXPLAIN ANALYZE): fixed N+1 queries, refactored legacy code, added composite, partial and covering indexes with zero-downtime migrations (AddIndexConcurrently)
- Domain event bus on Kafka with a unified header schema (messageType, trace ID, correlation ID); designed the integration contract with another team on top of it
- Moved document generation from synchronous to asynchronous: template parameter validation, optimized data aggregation, Kafka event publishing through Celery on `transaction.on_commit`
- Partner system integration: Celery background tasks, JWT with automatic access/refresh token renewal, retries, timeouts, Circuit Breaker (pybreaker), redelivery of unsent data
- Extended JWT authentication (cookie fallback for safe methods), fixing a long-standing auth issue for native browser requests and WebSockets; moved permission logic into DRF permission classes
- Market median price API on supplier offers (PostgreSQL aggregation: Median, ArrayAgg, BoolOr), atomic contract updates across domains
- Backward-compatible schema changes and large-scale production data processing (management commands, `queryset.iterator()`, `bulk_update`)
- OpenAPI documentation (drf-spectacular), including separate specs for partner companies based on their role-based access; code review

`Django` `DRF` `PostgreSQL` `Celery` `Redis` `Kafka` `Docker` `GitLab CI/CD`

---

### 🛒 Python Backend Developer — LANIT
*October 2021 — July 2024*

A B2B e-commerce platform with a microservice architecture for corporate clients: catalog, orders, payments, inventory, customer account and support chat.

- Designed and built core platform components on FastAPI, from a catalog with Redis caching to inventory management, connected through an API Gateway over gRPC
- Integrated a payment system with webhook signature verification, replay attack protection and idempotency, eliminating double charges
- Implemented Transactional Outbox and asynchronous payment processing over RabbitMQ with retries and a dead letter queue, guaranteeing delivery of every payment event
- Built atomic deductions from the customer's internal balance with PostgreSQL row locking — no race conditions, double charges or negative balances
- Introduced inventory sync on Celery with a Redis distributed lock, so customers always see up-to-date stock
- Built a WebSocket service on FastAPI with Redis Pub/Sub fan-out, scaling the support chat across multiple Kubernetes replicas without sticky sessions
- Moved exports and notifications to background tasks on Celery and RabbitMQ so long operations no longer block HTTP requests
- Optimized PostgreSQL queries for order history and stock with composite indexes and N+1 fixes, reaching **p95 under 300 ms**
- Covered code with unit and integration tests (pytest), did code review and set up GitLab CI/CD with automated checks and Kubernetes deployment

`FastAPI` `gRPC` `WebSockets` `PostgreSQL` `SQLAlchemy` `Redis` `RabbitMQ` `Celery` `Docker` `Kubernetes` `GitLab CI/CD`

---

## 🛠️ Open-source / pet projects

### [Async Payment Processing Service](https://github.com/Axierrerer/async-payment-process)
Payment-provider-style microservice: accepts payments via a REST API (`202 Accepted`), processes them asynchronously through an emulated payment gateway and notifies merchants via signed webhooks.
- **Transactional Outbox** — payment and event are written in one transaction; a separate relay publishes events with publisher confirms and `mandatory` routing, so no event is lost or silently dropped
- **Idempotency** — `Idempotency-Key` header plus request hash protects against duplicate payments; idempotent consumer for at-least-once delivery
- **Retries & DLQ** — exponential backoff via per-delay TTL retry queues (2s → 4s → 8s), Dead Letter Queue for messages that failed all attempts
- **Clean layering** — domain entities with business invariants, use cases, Unit of Work, repositories

`FastAPI` `Pydantic v2` `SQLAlchemy 2.0 (async)` `PostgreSQL` `RabbitMQ` `FastStream` `Alembic` `Docker`

### [Scalable WebSocket Chat](https://github.com/Axierrerer/websocket-chat)
Real-time chat on FastAPI WebSockets that scales horizontally: several app instances run behind a load balancer, and a message sent to one replica reaches every client of that chat on all replicas.
- **Cross-instance fan-out via Redis Pub/Sub** — each message is published to a `chat:{chat_id}` channel; every instance runs a listener on `PSUBSCRIBE chat:*` and broadcasts to its local connections
- **Connection management** — a dedicated manager tracks connections per chat; the Redis listener starts and stops with the app lifespan
- **Validated events** — incoming messages are validated with Pydantic schemas; invalid ones are logged and skipped without dropping the connection
- **Dependency injection** — dependencies are wired through a DI container (punq), keeping transport, infrastructure and config decoupled
- **Quality** — unit tests plus integration tests against a real Redis via Testcontainers, strict mypy, ruff; runs with Docker Compose (app waits for the Redis healthcheck)

`Python 3.14` `FastAPI` `WebSockets` `asyncio` `Redis Pub/Sub` `Pydantic v2` `punq` `pytest` `Testcontainers` `Docker`

---

## 🧰 Tech stack

**Languages & frameworks**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![asyncio](https://img.shields.io/badge/asyncio-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-A30000?style=flat-square&logo=django&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy_2.0-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-6BA539?style=flat-square&logo=python&logoColor=white)

**APIs & protocols**
![REST](https://img.shields.io/badge/REST_API-4A4A4A?style=flat-square&logo=openapiinitiative&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white)
![WebSockets](https://img.shields.io/badge/WebSockets-010101?style=flat-square&logo=socketdotio&logoColor=white)
![OpenAPI](https://img.shields.io/badge/OpenAPI-6BA539?style=flat-square&logo=openapiinitiative&logoColor=white)

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
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![GitLab CI](https://img.shields.io/badge/GitLab_CI/CD-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-F46800?style=flat-square&logo=grafana&logoColor=white)
