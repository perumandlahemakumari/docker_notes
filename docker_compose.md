
# Docker & Docker Compose Setup for Multi-Service Application

This project demonstrates setting up Docker and Docker Compose on a Linux server and running two different sets of services:

1. **Basic Service Deployment using Prebuilt Docker Images**
2. **Custom Paytm-like Microservices Deployment (Bank, Bus, Movie Booking)**

---

## 📦 Step 1: Docker & Docker Compose Installation

Install Docker and Docker Compose on a Linux system:

```bash
# Install Docker
yum install docker -y
systemctl start docker

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Verify installation
docker-compose --version
```

---

## 🚀 Step 2: Deploying Prebuilt Services (First `compose.yaml`)

Create a `compose.yaml` file:

```yaml
version: "3"
services:
  devops:
    image: suneel09/app
    ports:
      - "2345:80"
  Balu:
    image: suneel09/medical
    ports:
      - "3456:80"
  Hema:
    image: suneel09/food
    ports:
      - "4567:80"
```

Start the containers:

```bash
docker-compose up -d
docker ps -a
```

---

## 🛠️ Step 3: Custom Paytm-Like Microservices (Bank, Bus, Movie)

Directory structure:

```
paytm/
├── bank/
│   ├── Dockerfile
│   └── index.html
├── bus/
│   ├── Dockerfile
│   └── index.html
├── movie/
│   ├── Dockerfile
│   └── index.html
└── compose.yaml
```

Each service has the same Dockerfile:

```dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html
```

### HTML Content

**bank/index.html**
```html
<h1> This is Bank transactions app </h1>
```

**bus/index.html**
```html
<h1> This is Bus booking app, We have special offer get 50% off who come to offline </h1>
```

**movie/index.html**
```html
<h1> This is Movie tickets booking app </h1>
```

### `compose.yaml` for Paytm App

```yaml
version: "3"
services:
  svc1:
    build: ./bank/
    ports:
      - "9999:80"
  svc2:
    build: ./bus/
    ports:
      - "8888:80"
  svc3:
    build: ./movie/
    ports:
      - "7777:80"
```

### Run Paytm Services

```bash
cd paytm
docker-compose build
docker-compose up -d
docker ps
```

---

## 🧹 Clean Up

To stop and remove all containers:

```bash
docker-compose down
```

---

## 📝 Logs and Debugging

```bash
docker-compose logs
docker-compose config
docker-compose images
```
