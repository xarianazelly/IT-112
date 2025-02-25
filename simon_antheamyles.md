# DOCKER INSTALLATION AND CONTAINER CREATION ON A LINUX SYSTEM
 Here's the step by step documentation from installing docker to creating container with explanation:
<br><br>
## DOCKER INSTALLATION
### 1. Update System Packages
Before installing Docker, update your package list to ensure you get the latest version of the software:
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Install Required Dependencies
Install required dependencies to allow apt to use repositories over HTTPS:
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

### 3. Add Docker’s Official GPG Key
Add Docker's GPG key to verify the authenticity of the package:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### 4. Add Docker Repository
Add the Docker repository to your system’s sources list:
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 5. Install Docker Engine
Update the package list again and install Docker:
```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

### 6. Verify Docker Installation
Check if Docker is installed correctly by running:
```bash
docker --version
```

Enable and start the Docker service:
```bash
sudo systemctl enable docker
sudo systemctl start docker
```

Verify Docker is running:
```bash
sudo systemctl status docker
```

### 7. Add User to Docker Group (Optional)
To use Docker without `sudo`, add your user to the `docker` group:
```bash
sudo usermod -aG docker $USER
newgrp docker
```    
<br><br>
## CONTAINER CREATION
### 1. Create a Docker Container
Now, create a Linux-based Docker container and name it with your last name (e.g., `simon`).

Pull a base Linux image (e.g., Ubuntu):
```bash
docker pull ubuntu
```

Create and run a container named `simon`:
```bash
docker run -dit --name simon ubuntu
```

### 2. Verify Container Status
Check if the container is running:
```bash
docker ps
```

To list all containers, including stopped ones:
```bash
docker ps -a
```

### 3. Access the Running Container
To enter the container shell:
```bash
docker exec -it simon bash
```

### 4. Stop and Remove Container
To stop the container:
```bash
docker stop simon
```

To remove the container:
```bash
docker rm simon
```



