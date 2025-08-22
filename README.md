# 🔗 Scalable URL Shortener (Bitly-style)

A production-ready, **scalable URL shortener** built with **.NET 8**, **EF Core**, **Redis**, and **Docker**.  
This project demonstrates **system design principles** like caching, rate limiting, monitoring, and clean architecture.

---

## 🚀 Features
- Shorten + redirect endpoints
- Expiration dates for shortened URLs
- Analytics: click count, last accessed time
- Redis caching for fast lookups
- Rate limiting middleware to prevent abuse
- Logging with Serilog
- Monitoring with Prometheus + Grafana
- Clean Architecture + SOLID principles
- CI/CD pipeline (GitHub Actions)

---

## 🏗️ Architecture
![Architecture Diagram](./docs/architecture-diagram.png)

- **API Layer:** Exposes REST endpoints  
- **Application Layer:** Handles use cases (CQRS style)  
- **Domain Layer:** Entities + business rules  
- **Infrastructure Layer:** EF Core (SQL Server/Postgres), Redis, Logging  
- **Background Jobs:** Expiration cleanup + analytics aggregation  

---

## 📂 Project Structure
```
UrlShortener/
│── src/
│   ├── UrlShortener.Api/              # Web API (controllers, middleware, DI)
│   ├── UrlShortener.Application/      # Application layer (DTOs, services, CQRS, business rules)
│   ├── UrlShortener.Domain/           # Domain entities, interfaces
│   ├── UrlShortener.Infrastructure/   # EF Core, Redis, Logging, Repository implementations
│   └── UrlShortener.BackgroundJobs/   # Expiration cleanup, analytics jobs (Hangfire/Quartz)
│
│── tests/
│   ├── UrlShortener.UnitTests/        # Unit tests
│   ├── UrlShortener.IntegrationTests/ # API + DB + Redis tests
│
│── docker/
│   ├── docker-compose.yml             # API + SQL + Redis setup
│   └── grafana-prometheus/            # Monitoring setup
│
│── .github/workflows/                 # GitHub Actions CI/CD pipelines
│
│── docs/
│   ├── architecture-diagram.png
│   ├── system-design.md
│   └── api-docs.md
│
│── README.md
│── LICENSE
```


---

## 🔧 Tech Stack
- **.NET 8** – Web API
- **EF Core** – Database ORM
- **SQL Server/Postgres** – Primary DB
- **Redis** – Caching layer
- **Serilog** – Structured logging
- **Prometheus + Grafana** – Monitoring
- **Docker & Docker Compose** – Containerization
- **GitHub Actions** – CI/CD

---

## 📌 API Endpoints
- `POST /api/shorten` → Shorten a URL (with optional expiration date)
- `GET /{shortCode}` → Redirect to original URL
- `GET /api/analytics/{shortCode}` → Get click count + last accessed
- `DELETE /api/{shortCode}` → Delete shortened URL

---

## ⚙️ Setup & Run

### Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/)
- [Docker](https://www.docker.com/)
- [Redis](https://redis.io/)
- SQL Server

### Run Locally
```bash
git clone https://github.com/a1excpunk/UrlShortener.git
cd UrlShortener
docker-compose up -d
dotnet run --project src/UrlShortener.Api
```

API will be available at: http://localhost:5000