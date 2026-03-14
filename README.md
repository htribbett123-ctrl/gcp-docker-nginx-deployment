## 🐳 Deploying Nginx in Docker on a Google Cloud VM

![Google Cloud](https://img.shields.io/badge/Google%20Cloud-VM%20Instance-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04%20LTS-orange)
![Linux](https://img.shields.io/badge/Linux-CLI-important)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green)
![Networking](https://img.shields.io/badge/Networking-Port%20Mapping-yellow)
![Firewall](https://img.shields.io/badge/GCP-Firewall%20Rules-red)
![Automation](https://img.shields.io/badge/DevOps-Hands--On-blueviolet)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)



A complete DevOps workflow demonstrating VM provisioning, package installation, Docker setup, containerized Nginx, port mapping, and Google Cloud firewall configuration

---

## 📌 Overview
This project walks through deploying a live Nginx web server inside a Docker container running on a Google Cloud Compute Engine VM.
You will learn:
- Creating a VM using Google Cloud Shell
- Updating and securing the VM
- Installing Nginx
- Installing Docker
- Running Nginx inside a Docker container
- Mapping ports for external access
- Configuring Google Cloud firewall rules
- Testing the deployment from a browser

  
## 🏗️ 1. Create a Google Cloud VM
Run in Cloud Shell:
```bash
gcloud compute instances create ubuntu-basic \
  --zone=us-central1-a \
  --machine-type=e2-micro \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud
```
  
## 🔧 2. Update the V
```bash
sudo apt-get update && sudo apt-get upgrade -y
```

## 🌐 3. Install Nginx
```bash
sudo apt install nginx -y
```

## check Nginx status
```bash
systemctl status nginx
```

## Test locally
```bash
curl 127.0.0.1:
```
You should see the default Nginx HTML response.

## 🐳 4. Install Docker
```bash
sudo apt-get install docker.io -y:
systemctl status docker
```

## Pull the nginx image
```bash
sudo docker pull nginx
```
## 🔐 5. Fix Docker Permission
If you see a “permission denied” error, add your user to the Docker group:
```bash
sudo usermod -aG docker $USER
exit
```
Re‑SSH into the VM.

## 🟦 6. Run Nginx in Docker

Foreground mode (shows logs)
```bash
docker run nginx
```
Background mode (recommended):
```bash
docker run -d -p 8080:80 nginx
```
Check running containers:
```bash
docker ps
```

## 🌍 7. Configure Google Cloud Firewall
Add a network tag:
```bash
gcloud compute instances add-tags ubuntu-basic \
  --tags=http-server \
  --zone=us-central1-a
```
Create a firewall rule
```bash
gcloud compute firewall-rules create allow-http \
  --allow=tcp:8080 \
  --target-tags=http-server
```
## 🌐 8. Test External Access
Test from inside the VM:
```bash
curl http://<YOUR_PUBLIC_IP>:8080
```
Will show the HTML

Replace with your VM’s public IP:
```bash
http://<YOUR_PUBLIC_IP>:8080
```

## You should see a welcome to Ngnix



