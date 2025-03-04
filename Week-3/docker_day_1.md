# Docker Day 1

## **Introduction to Docker**
Docker is a powerful tool for developing and deploying applications efficiently. It is lightweight and reduces dependencies, making applications run faster than virtual machines. Docker acts like a **shipping container for software**.

### **Key Concepts**
- **Docker Image**: A blueprint for containers, containing all dependencies.
- **Docker Container**: A running instance of an image, providing an isolated environment.
- **Docker Components**:
  1. **Docker CLI**: Command-line interface for managing Docker.
  2. **Docker Daemon**: Background service managing containers.
  3. **Docker Registry**: Storage for Docker images (e.g., Docker Hub).

## **Installing Docker on Ubuntu**
```sh
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
sudo usermod -aG docker $USER
```

## **Verifying Docker Installation**
```sh
docker --version
```

## **Creating a Docker Image**
```sh
mkdir python-dock-project
cd python-dock-project/
mkdir src tests
touch src/__init__.py src/main.py requirements.txt Dockerfile .dockerignore docker-compose.yml
```

### **Creating a Virtual Environment and Installing Dependencies**
```sh
python3 -m venv env
source env/bin/activate
pip install -r requirements.txt
```

## **Building and Running a Docker Image**
```sh
docker build -t python-docker-app .
docker run -p 5000:5000 python-docker-app
```

## **Pushing Images to Docker Hub**
```sh
docker login

docker tag python-docker-app:latest username/python-docker-app:v1
docker push username/python-docker-app:v1
```

## **Using Docker Compose**
```sh
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose up --build
```

## **Summary**
- Learned about Docker images and containers.
- Installed Docker and created a simple containerized application.
- Built, ran, and pushed Docker images to Docker Hub.
- Explored Docker Compose for managing multiple containers.
