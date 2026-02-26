# MEAN Stack CRUD Application

A full-stack CRUD application built with MongoDB, Express, Angular 15, and Node.js. Deployed on AWS EC2 using Docker, Nginx, and GitHub Actions CI/CD.

---

## Tech Stack
- **MongoDB** - Database
- **Express** - Backend REST API
- **Angular 15** - Frontend
- **Node.js** - Runtime
- **Docker** - Containerization
- **Nginx** - Reverse Proxy
- **GitHub Actions** - CI/CD Pipeline
- **AWS EC2** - Cloud Hosting

---

## Features
- Add new tutorials
- View all tutorials
- Edit existing tutorials
- Delete tutorials
- Search tutorials by title

---

## Project Structure

```
mean-app/
├── backend/            ← Node.js + Express API
│   └── Dockerfile
├── frontend/           ← Angular 15
│   ├── Dockerfile
│   └── nginx.conf
├── nginx/              ← Reverse proxy config
│   └── nginx.conf
├── .github/workflows/  ← CI/CD pipeline
│   └── deploy.yml
├── docker-compose.yml
└── README.md
```

---

## How to Run Locally

### 1. Clone the repository
```
git clone https://github.com/aiman-riaz/mean-app.git
cd mean-app
```

### 2. Start all containers
```
docker compose up -d
```

### 3. Open in browser
```
http://localhost
```

---

## Deployment on AWS EC2

### 1. Create Ubuntu 22.04 EC2 instance on AWS
- Allow port 22 (SSH) and port 80 (HTTP) in security group

### 2. SSH into the VM
```
ssh -i your-key.pem ubuntu@YOUR_VM_IP
```

### 3. Install Docker
```
sudo apt update -y
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker ubuntu
sudo apt install docker-compose-plugin -y
```

### 4. Clone and deploy
```
git clone https://github.com/aiman-riaz/mean-app.git ~/mean-app
cd ~/mean-app
sudo docker compose up -d
```

### 5. Verify containers are running
```
sudo docker compose ps
```

### 6. Open in browser
```
http://YOUR_VM_IP
```

---

## CI/CD Pipeline
Every time code is pushed to the main branch, GitHub Actions automatically:
1. Builds Docker images for frontend and backend
2. Pushes images to Docker Hub
3. SSHs into AWS VM and restarts containers with latest images

### GitHub Secrets Required
| Secret | Description |
|---|---|
| DOCKER_USERNAME | Docker Hub username |
| DOCKER_PASSWORD | Docker Hub access token |
| VM_HOST | AWS EC2 public IP |
| VM_USER | ubuntu |
| VM_SSH_KEY | Private SSH key |

---

## Infrastructure
- **Cloud:** AWS EC2 Ubuntu 22.04
- **Containers:** Docker Compose with 4 services
  - MongoDB
  - Node.js Backend
  - Angular Frontend
  - Nginx Reverse Proxy
- **Reverse Proxy:** Nginx on port 80
- **Database:** MongoDB as Docker container

---
