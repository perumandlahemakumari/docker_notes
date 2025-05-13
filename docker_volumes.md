
# Docker Volume and Container Management Guide

This guide documents a step-by-step process of working with Docker containers, volumes, and mounts in a Linux environment.

---

## 🔧 Docker Installation & Startup

```bash
yum install docker -y
systemctl start docker
```

---

## 📦 Creating and Using Docker Volumes

### Step 1: Create a container with a volume
```bash
docker run -itd --name cont1 -v /suneel ubuntu
docker exec -it cont1 bash
ll
rm -rf Suneel/
cd Suneel/ && touch git{1..5}
ll && exit
```

### Step 2: Check volumes and inspect container
```bash
docker volume ls
docker inspect cont1
```

### Step 3: Share volume with another container
```bash
docker run -itd --name cont2 --privileged --volumes-from=cont1 ubuntu
docker exec -it cont2 bash
ll && cd Suneel/
touch aws gcp azure && exit
```

### Step 4: Verify shared volume from original container
```bash
docker exec -it cont1 bash
cd Suneel/ && ls
exit
```

---

## 📁 Bind Mount from Host to Container

```bash
mkdir paytm
cd paytm/
touch wipro google facebook
ll
docker run -itd --name cont3 -v $(pwd):/pranith ubuntu
docker exec -it cont3 bash
cd pranith/ && ll && touch Suneel.txt hema.doc
exit
```

---

## 🧹 Container and Volume Cleanup

```bash
docker volume ls
docker kill $(docker ps)
docker container prune
docker volume ls
```

---

## 🔍 Inspect Specific Volume Data

```bash
docker volume inspect <VOLUME_ID>
cd /var/lib/docker/volumes/<VOLUME_ID>/_data
ll
```

---

## 🌐 Host-Served HTML via Docker + Volume

```bash
cd ~
mkdir app/
cd app/
vi index.html
# Add:
# <h1> welcome to page </h1>
# <h2> Deployment through docker volumes </h2>
docker run -itd --name cont1 -p 1234:80 -v $(pwd):/usr/local/apache2/htdocs httpd
# Visit: http://<your-ip>:1234
```

---

## 🧽 Volume Cleanup and Mounting

```bash
docker volume rm <OLD_VOLUME_ID>
docker volume prune
docker volume create kiran
docker volume ls
cd /var/lib/docker/volumes/kiran/_data
touch suneel{1..2}
```

---

## 🔗 Mount Volume Using `--mount`

```bash
docker run -itd --name cont3 --mount source=kiran,destination=/mahesh ubuntu
docker exec -it cont3 bash
cd /mahesh/
ll
```

---

## ✅ Summary

You learned how to:
- Install and start Docker
- Create and inspect Docker volumes
- Share volumes between containers
- Use bind mounts from host directories
- Serve content via Apache using Docker volumes
- Clean up Docker resources

---

**Note**: Replace `<VOLUME_ID>` with the actual ID from `docker volume ls`.

