# MetroCrawl

**A High-Performance Distributed Web Crawling Engine**

MetroCrawl is a production-grade distributed web crawling framework built on top of Scrapy, Redis, and Apache Kafka. It enables scalable, coordinated, and on-demand web scraping across distributed clusters with real-time data processing pipelines.

> **PROPRIETARY SOFTWARE** -- Copyright (c) 2024-2026 Digital Metro. All Rights Reserved.
> Unauthorized use, reproduction, or distribution is strictly prohibited.
> See [LICENSE](LICENSE) for full terms.

---

## Architecture Overview

MetroCrawl employs a microservices architecture with four core components orchestrated through Redis and Kafka:

```
                    +------------------+
                    |   Kafka Monitor  |
                    |  (Ingestion API) |
                    +--------+---------+
                             |
                    +--------v---------+
                    |   Apache Kafka   |
                    |   (Message Bus)  |
                    +--------+---------+
                             |
              +--------------+--------------+
              |              |              |
     +--------v---+  +-------v----+  +------v-------+
     |  Crawler   |  |  Crawler   |  |   Crawler    |
     | Instance 1 |  | Instance 2 |  |  Instance N  |
     +--------+---+  +-------+----+  +------+-------+
              |              |              |
              +--------------+--------------+
                             |
                    +--------v---------+
                    |      Redis       |
                    | (Coordination &  |
                    |   Throttling)    |
                    +--------+---------+
                             |
                    +--------v---------+
                    |  Redis Monitor   |
                    | (Stats & Control)|
                    +--------+---------+
                             |
                    +--------v---------+
                    |   REST Service   |
                    |  (External API)  |
                    +------------------+
```

## Core Features

- **Dynamic On-Demand Crawling** -- Submit arbitrary URLs for crawling via Kafka or REST API
- **Horizontal Scalability** -- Scale crawler instances across single or multiple machines seamlessly
- **Distributed Rate Limiting** -- Coordinated throttling across all crawlers behind the same IP address
- **Domain-Based Queue Management** -- Intelligent prioritization and scheduling per domain
- **Real-Time Data Pipeline** -- Kafka-based data bus for job submission, monitoring, and results
- **Cross-Spider Coordination** -- Independent spiders can yield requests to each other
- **Persistent State** -- Crawl state persists across job restarts and failures
- **Concurrent Job Execution** -- Run multiple scraping jobs simultaneously
- **Pluggable Architecture** -- Extensible plugin system for Kafka Monitor and Redis Monitor
- **Production Monitoring** -- Built-in statistics collection, ELK stack integration, and health monitoring
- **Docker Native** -- Full Docker Compose support for rapid deployment and scaling
- **REST API** -- RESTful interface for external system integration

## Technology Stack

| Component | Technology |
|-----------|-----------|
| Crawling Engine | Scrapy |
| Message Broker | Apache Kafka |
| Coordination Layer | Redis |
| Service Discovery | Apache Zookeeper |
| Containerization | Docker / Docker Compose |
| Monitoring | ELK Stack (Elasticsearch, Logstash, Kibana) |
| Language | Python 3.6+ |

## Quick Start (Docker)

### Prerequisites

- [Docker](https://www.docker.com/) and Docker Compose installed

### Launch the Cluster

1. **Start all services:**
   ```bash
   docker-compose up -d --build
   ```

2. **Monitor crawl results:**
   ```bash
   docker-compose exec kafka_monitor python kafkadump.py dump -t demo.crawled_firehose -ll INFO
   ```

3. **Submit a crawl request:**
   ```bash
   curl localhost:5343/feed \
     -H "content-type:application/json" \
     -d '{"url": "http://example.com", "appid": "testapp", "crawlid": "job001"}'
   ```

4. **View results** in the Kafka monitor terminal.

## Project Structure

```
metrocrawl/
|-- crawler/          # Scrapy-based distributed crawlers
|-- kafka-monitor/    # Kafka ingestion and API gateway
|-- redis-monitor/    # Redis-based monitoring and statistics
|-- rest/             # REST API service
|-- utils/            # Shared utilities library (scutils)
|-- docker/           # Docker build configurations
|-- elk/              # ELK stack integration
|-- docs/             # Sphinx documentation
|-- docker-compose.yml
|-- requirements.txt
`-- version.py
```

## Documentation

Full documentation is available in the `docs/` directory. Build locally with Sphinx:

```bash
cd docs
make html
```

## Version

Current Release: **2.0.0**

---

## Legal

This software is proprietary and confidential. Copyright (c) 2024-2026 Digital Metro.
All rights reserved. See [LICENSE](LICENSE) for complete terms.

Developed and maintained by **Digital Metro**.
Contact: rajkaran@digitalmetro.dev
