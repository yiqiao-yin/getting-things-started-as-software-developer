# Getting Started with Docker Desktop on Windows

## 1. Installing Docker Desktop on Windows

### Step 1: Download Docker Desktop
- Download from the official website: [Docker for Windows](https://www.docker.com/products/docker-desktop)
- Ensure your system meets the requirements:
  - **Windows 10/11 Pro, Enterprise, or Education (64-bit)** with **WSL 2** enabled.
  - **Windows Home** users need to install **WSL 2 Backend**.

### Step 2: Install Docker Desktop
- Run the installer and follow the on-screen instructions.
- Choose the **WSL 2 Backend** for better performance.
- Restart your system after installation.

### Step 3: Verify Installation
Run the following command in **PowerShell** or **Command Prompt**:
```sh
docker --version
```

If Docker is installed correctly, it will return the installed version.

### Step 4: Enable WSL 2 (if not already enabled)
1. Open PowerShell as Administrator and run:
   ```sh
   wsl --install
   ```
2. Set WSL 2 as the default version:
   ```sh
   wsl --set-default-version 2
   ```

To check the installed WSL versions, run:
```sh
wsl -l -v
```

---

## 2. Key Docker Commands

### **System & Version Commands**
```sh
docker version        # Show Docker version
docker info           # Show system-wide information
docker system prune  # Clean up unused data
```

### **Container Management**
```sh
docker run -d -p 8080:80 nginx  # Run an Nginx container in detached mode
docker ps                        # List running containers
docker ps -a                     # List all containers
docker stop <container_id>       # Stop a running container
docker rm <container_id>         # Remove a container
docker logs <container_id>       # View logs of a container
```

### **Image Management**
```sh
docker images                  # List all Docker images
docker pull ubuntu             # Download a Docker image
docker rmi <image_id>          # Remove an image
docker build -t myapp .        # Build an image from Dockerfile
docker tag myapp myrepo/myapp  # Tag an image for pushing
docker push myrepo/myapp       # Push image to Docker Hub
```

### **Volume Management**
```sh
docker volume create myvolume  # Create a new volume
docker volume ls               # List volumes
docker volume rm myvolume      # Remove a volume
```

### **Network Management**
```sh
docker network ls              # List networks
docker network create mynet    # Create a custom network
docker network rm mynet        # Remove a network
docker network inspect mynet   # Inspect network details
```

---

## 3. Writing Dockerfiles

### **Basic Python Application**
```dockerfile
# Use an official Python runtime as a parent image
FROM python:3.9

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container
COPY . /app

# Install dependencies
RUN pip install -r requirements.txt

# Command to run the application
CMD ["python", "app.py"]
```

### **Node.js Application**
```dockerfile
FROM node:16
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

### **Multi-Stage Build for a Go App**
```dockerfile
# Build stage
FROM golang:1.18 as builder
WORKDIR /app
COPY . .
RUN go build -o myapp

# Final stage
FROM alpine
WORKDIR /root/
COPY --from=builder /app/myapp .
CMD ["./myapp"]
```

---

## 4. Running Containers with Custom Configurations

### **Running a Container with Volume Mounting**
```sh
docker run -d -v C:\Users\myfolder:/data -p 5000:5000 myapp
```

### **Running a Container in Interactive Mode**
```sh
docker run -it ubuntu /bin/bash
```

### **Running a Container in Detached Mode**
```sh
docker run -d nginx
```

---

## 5. Using Docker Compose

### **Sample `docker-compose.yml` for a Flask App**
```yaml
version: '3.8'
services:
  web:
    image: python:3.9
    working_dir: /app
    volumes:
      - .:/app
    ports:
      - "5000:5000"
    command: python app.py
```

### **Starting and Stopping Containers with Docker Compose**
```sh
docker-compose up -d   # Start containers in detached mode
docker-compose down    # Stop and remove containers
```

---

## 6. Debugging & Troubleshooting

### **Checking Container Logs**
```sh
docker logs <container_id>
```

### **Entering a Running Container**
```sh
docker exec -it <container_id> powershell   # Windows-based images
docker exec -it <container_id> /bin/bash   # Linux-based images
```

### **Restarting Docker**
```sh
Restart-Service docker   # Restart Docker from PowerShell
```

---

## 7. Additional Resources
- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)

By following this guide, you should be able to get started with Docker on Windows effectively. 🚀

