
# Docker Networking - Fresher Notes

This document provides beginner-level notes and commands to understand and practice Docker networking concepts.

---

## 1. 🐳 Install Docker and Start Service

**Command:**
```bash
yum install docker -y && systemctl start docker
```

**Description:**
Installs Docker and starts the Docker service.

---

## 2. 🚀 Running Containers

**Commands:**
```bash
docker run -itd --name cont1 ubuntu
docker run -itd --name cont2 ubuntu
```

**Description:**
Runs two containers (`cont1` and `cont2`) in interactive detached mode using the Ubuntu image.

---

## 3. 🔍 Inspecting Containers

**Commands:**
```bash
docker inspect cont1
docker inspect cont2
```

**Description:**
Displays detailed information about the containers’ configuration and networking.

---

## 4. 🌐 Creating Docker Networks

**Commands:**
```bash
docker network create frontend
docker network create backend
docker network ls
```

**Description:**
Creates two custom networks named `frontend` and `backend`, and lists all existing networks.

---

## 5. 📡 Running Containers on Custom Networks

**Commands:**
```bash
docker run -itd --name hema --network=frontend ubuntu
docker run -itd --name devops --network=backend ubuntu
```

**Description:**
Runs containers on specific custom networks.

---

## 6. 🔎 Inspect and Interact

**Commands:**
```bash
docker inspect hema
docker inspect devops
docker exec -it hema bash
```

**Description:**
Inspects the containers and allows terminal access to `hema` container.

---

## 7. 🔁 Connect Containers to Multiple Networks

**Commands:**
```bash
docker network connect backend hema
docker network connect frontend devops
docker exec -it hema bash
docker exec -it devops bash
```

**Description:**
Connects `hema` to the `backend` network and `devops` to the `frontend` network, enabling multi-network communication.

---

📝 **Note:** You can verify the network connections by running `ip a` inside containers or using `ping` to test connectivity between containers.
