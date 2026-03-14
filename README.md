## 🐳 Deploying Nginx in Docker on a Google Cloud VM

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
gcloud compute instances create ubuntu-basic \
  --zone=us-central1-a \
  --machine-type=e2-micro \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud
  
## 🔧 2. Update the V
sudo apt-get update && sudo apt-get upgrade -y

## 🌐 3. Install Nginx

sudo apt install nginx -y
check status:
systemctl status nginx

Test locally:
curl 127.0.0.1:
You should see the default Nginx HTML response.

## 🐳 4. Install Docker

sudo apt-get install docker.io -y:
systemctl status docker:

Pull the nginx image:
sudo docker pull nginx

