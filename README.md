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

Python backend developer with **4+ years** of commercial experience building B2B systems: e-commerce platforms and procurement/supply automation for the aviation industry.

I design and build microservices and distributed systems with Django, FastAPI, Kafka and Temporal. My focus is performance and reliability: I've made APIs 10x+ faster, cut the main application's CPU load by ~30% and built resilient integrations with payment and external systems. I own services end to end — from data and API design to release, monitoring and production support.

📍 Based in Georgia (UTC+4) · 🌍 Open to remote Python backend roles

---

## ⚡ Selected results

- 🚀 Made a business-critical API **10x+ faster** (8–12 s → 400–800 ms); its heaviest SQL query went from **8 s to 50–60 ms** after replacing per-row subqueries with window functions in CTEs, eliminating N+1 queries and adding indexes with zero downtime
- 🏗️ Designed and shipped **5 production services** on FastAPI, Kafka and Temporal — from data and API design to Docker, GitLab CI/CD and deployment to dev, stage and prod
- 📉 Cut main application **CPU load by ~30%** by extracting document generation from the Django monolith into a dedicated service, which another development department now uses too
- ⚡ Made XLSX → PDF conversion **~12x faster** (4–5 s → 300–400 ms) by replacing a LibreOffice process per file with a persistent conversion server (unoserver)
- 🔁 Built reliable async processing across Kafka and Temporal: idempotency by correlation ID, retries on transient errors, end-to-end trace ID across HTTP, Kafka and Temporal for fast debugging in Loki
- 🤖 Refactored a **20K+ line** document generation codebase with AI tooling onto a flexible contract for multiple external systems — **zero regressions**, verified by golden-file comparison of all existing outputs
- 🚦 Built a **Redis-based sliding window rate limiter** (sorted sets, MULTI/EXEC) enforcing limits consistently across multiple service instances

---

## 🧩 Key projects

> Commercial projects are under NDA, so their code is private. Here is what I worked on.

### ✈️ ERP for an aviation parts company
Internal ERP used by hundreds of employees across a group of companies: orders, parts accounting, warehouses, RFQs, commercial offers, invoices and pricing. Optimized the heaviest APIs (10x+ faster), built 20+ per-supplier Excel/PDF business documents with dynamic page layout, and integrated an external quoting system (JWT auth with token refresh, retries).
`Django` `DRF` `PostgreSQL` `Celery` `Redis` `Docker` `GitLab CI/CD`

### 📄 Document generation service
Event-driven service extracted from the monolith (−30% CPU): consumes Kafka events, generates Excel and PDF documents from per-supplier templates, stores files in S3 and reports results back to the ERP via Temporal. At-least-once delivery with idempotent processing; serves two external systems. Later refactored with golden-file regression testing.
`Python` `Kafka` `Temporal` `openpyxl` `LibreOffice / unoserver` `MinIO (S3)` `Docker`

### 🔎 Company search for data verification
Search over a directory of 50K+ companies feeding an ML model that checks data reliability: exact search (B-tree) and fuzzy search with relevance scoring (pg_trgm + GIN). Later moved to Elasticsearch (fuzzy matching, custom analyzers, zero-downtime reindexing) to avoid loading the ERP's main database.
`FastAPI` `PostgreSQL` `pg_trgm` `Elasticsearch` `Temporal`

### 🔁 Analytics platform: S2S integration
Temporal orchestrator (a workflow per business task, idempotent Telegram notifications to managers) plus a FastAPI service reading analytics data, with JWT auth, a Redis sliding window rate limiter and Elasticsearch search indexed via Celery Beat.
`Temporal` `FastAPI` `PostgreSQL` `Elasticsearch` `Redis` `Celery`

### 🔎 Reusable Elasticsearch events library
Internal Python library with overridable repositories for Pydantic models, built for reuse across services, with zero-downtime index changes.
`Python` `Pydantic` `Elasticsearch`

### 🛒 B2B e-commerce platform
Built core backend modules from scratch: catalog, customer account, payments and inventory. Payment provider integration (payments, top-ups, refunds) with signed webhooks, replay protection and idempotency; internal balance with atomic debits (no double charges or negative balance); inventory sync with atomic upserts and a Redis distributed lock; cache-aside caching in Redis.
`Django` `DRF` `PostgreSQL` `Celery` `RabbitMQ` `Redis` `S3`

---

## 🛠️ Open-source / pet projects

### [Async Payment Processing Service](https://github.com/Axierrerer/async-payment-process)
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
![asyncio](https://img.shields.io/badge/asyncio-3776AB?style=flat-square&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/DRF-A30000?style=flat-square&logo=django&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy_2.0-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-6BA539?style=flat-square&logo=python&logoColor=white)

**Data & messaging**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![asyncpg](https://img.shields.io/badge/asyncpg-4169E1?style=flat-square&logo=postgresql&logoColor=white)
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
