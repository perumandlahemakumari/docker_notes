Docker Networking - Fresher Notes
1. Install Docker and Start Service

Command:
    yum install docker -y && systemctl start docker
Description:
    Installs Docker and starts the Docker service.

2. Running Containers

Commands:
    docker run -itd --name cont1 ubuntu
    docker run -itd --name cont2 ubuntu
Description:
    Runs two containers (cont1 and cont2) in interactive detached mode using the Ubuntu image.

3. Inspecting Containers

Commands:
    docker inspect cont1
    docker inspect cont2
Description:
    Displays detailed information about the container’s configuration and networking.

4. Creating Docker Networks

Commands:
    docker network create frontend
    docker network create backend
    docker network ls
Description:
    Creates two custom networks named frontend and backend, and lists all networks.

5. Running Containers on Custom Networks

Commands:
    docker run -itd --name hema --network=frontend ubuntu
    docker run -itd --name devops --network=backend ubuntu
Description:
    Runs containers on specific custom networks.

6. Inspect and Interact

Commands:
    docker inspect hema
    docker inspect devops
    docker exec -it hema bash
Description:
    Inspects the containers and allows terminal access to 'hema'.

7. Connect Containers to Multiple Networks

Commands:
    docker network connect backend hema
    docker network connect frontend devops
    docker exec -it hema bash
    docker exec -it devops bash
Description:
    Connects 'hema' to backend and 'devops' to frontend, enabling multi-network communication.




