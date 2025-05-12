
🐳 Docker Swarm: Fresher Notes

📦 1. Install Docker & Start Service
-------------------------------------
yum install docker -y && systemctl start docker
- Installs Docker and starts the Docker service on a Linux system (RHEL/CentOS-based).

🌐 2. Initialize Docker Swarm
------------------------------
docker swarm init --advertise-addr 172.31.5.214
- Initializes the current machine as a Swarm manager.
- '--advertise-addr' tells other nodes where to join the swarm.

👥 3. Swarm Node Management
----------------------------
docker node ls
- Lists all nodes in the swarm (only works on manager).

🔍 4. View Services in Swarm
-----------------------------
docker service ls
- Shows all running services in the swarm.

🚀 5. Create a Service
-----------------------
docker service create --name paytm --publish 1234:80 nginx
- Creates a service called 'paytm' exposing Nginx on port 1234.

🧾 6. List Running Containers
------------------------------
docker ps
- Lists all running containers.

🛑 7. Kill a Container
-----------------------
docker kill <container_id>
- Stops a running container by ID.

🗑️ 8. Remove a Container
--------------------------
docker rm <container_id>
- Deletes a stopped container.

🌐 9. Create Custom Services
-----------------------------
docker service create --name swiggy --publish 2345:80 suneel09/medical
docker service create --name zomato --publish 3456:80 suneel09/food

⚙️ 10. Scale a Service
------------------------
docker service scale swiggy=2
- Increases the number of replicas to 2.

📋 11. View Tasks of a Service
-------------------------------
docker service ps swiggy

♻️ 12. Update or Rollback a Service
------------------------------------
docker service update --image suneel09/food swiggy
docker service rollback swiggy

📜 13. Logs and Inspect
------------------------
docker service logs swiggy
docker service inspect swiggy

🔐 14. Join Tokens for Swarm
-----------------------------
docker swarm join-token worker
docker swarm join-token manager

🧹 15. Remove Nodes and Services
---------------------------------
docker service rm swiggy
docker service rm paytm
docker node rm <node_id>

🧠 Tip: Use 'history' to recall all commands
--------------------------------------------
history

✅ All commands tested on Docker Swarm in a single-node setup (for practice/demo).
