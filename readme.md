# 🧪  Nginx Reverse Proxy + Docker Compose

This project demonstrates a reverse proxy setup using Docker Compose, where two backend services (Go and Python) are routed via an Nginx container. Each service exposes basic endpoints and includes health checks.

---

## 📁 Project Structure

.
├── docker-compose.yml
├── nginx/
│ └── default.conf
├── service_1/
│ ├── main.go
│ ├── go.mod
│ └── Dockerfile
├── service_2/
│ ├── app.py
│ ├── pyproject.toml
│ ├── requirements.txt
│ └── Dockerfile
└── README.md




---

## 🛠️ Tech Stack

- 🐳 Docker + Docker Compose
- 🐍 Python 3.12 + Flask (Service 2)
- 🧪 Go 1.22+ (Service 1)
- 🌐 Nginx as reverse proxy

---

## 🚀 How to Run

1. **Clone this repository**:
   ```bash
   git clone <repo-url>
   cd <repo-folder>

2. **Build and start all services:**:
   ```bash
   docker-compose up --build

3. **Access the services via Nginx reverse proxy:**:

    - http://localhost:8080/service1/ping
    - http://localhost:8080/service2/ping


## 🚀 🔄 Routing Logic
   Nginx listens on port 8080 and proxies based on path prefix:
   | Path Prefix | Target Container | Port |
   | ----------- | ---------------- | ---- |
   | `/service1` | `service1`       | 8001 |
   | `/service2` | `service2`       | 8002 |

   Nginx forwards headers and logs each request with timestamp and path.


## 🔍 Health Checks
    Each service exposes a /ping endpoint used for health checks:
    ```bash
    {"status": "ok", "service": "1"}
   
## Nginx logging
    All logs are viewable with:
    ```bash
    docker-compose logs nginx
    



