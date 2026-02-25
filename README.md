### Step 1 - Clone the Repository
```
git clone https://github.com/aiman-riaz/mean-app.git
cd mean-app
```

### Step 2 - Install Docker on Ubuntu VM
```
sudo apt update -y
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker ubuntu
sudo apt install docker-compose-plugin -y
```

### Step 3 - Deploy with Docker Compose
```
cd ~/mean-app
sudo docker compose up -d
```

### Step 4 - Verify Containers are Running
```
sudo docker compose ps
```
You should see 4 containers running:
- mean-app-mongo-1
- mean-app-backend-1
- mean-app-frontend-1
- mean-app-nginx-1

### Step 5 - Access the Application
```
http://YOUR_VM_IP
```
