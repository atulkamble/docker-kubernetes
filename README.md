**Docker & Kubernetes Setup and Notes** suitable for learning, sharing, or future reference. This version includes step-by-step instructions, grouped by environment and purpose:

---

# 🐳 **Docker + Kubernetes Setup & Commands**

---

# Architecture of k8s 

![Kubernetes Cluster Architecture](https://github.com/atulkamble/docker-kubernetes/raw/main/kubernetes-cluster-architecture.svg)


## 🖥️ **System Requirements & Prerequisites**

### ✅ BIOS Setup

* Enable **Virtualization Technology (VT-x)** in BIOS/UEFI.

### ✅ Windows Features (for Docker Desktop)

1. Open **“Turn Windows features on or off”**.
2. Enable:

   * ✅ Windows Subsystem for Linux (WSL)
   * ✅ Virtual Machine Platform
   * ✅ Windows Hypervisor Platform
3. Restart your system.

---

## ⚙️ **Install WSL on Windows**

Open **PowerShell as Administrator** and run:

```powershell
wsl --install
```

> ⚠️ Reboot after installation completes.

---

## 🐳 **Install Docker**

### 🪟 **On Windows (Docker Desktop)**

1. Download from:
   👉 [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

2. Install and **keep Docker Desktop running in background**.

3. Confirm installation:

```bash
docker --version
```

---

### 🐧 **On Ubuntu / WSL2**

```bash
sudo apt update -y
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

### 🧱 **On RedHat / CentOS / Amazon Linux**

```bash
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 📦 **Working with Docker**

### 👨‍💻 Clone Sample App

```bash
cd ~/Downloads
git clone https://github.com/atulkamble/pythonhelloworld.git
cd pythonhelloworld
```

### 🔍 Basic Docker Commands

```bash
docker images
docker container ls
```

### 🔑 Docker Hub

1. Sign up: [https://hub.docker.com](https://hub.docker.com)
2. Login from terminal:

```bash
docker login
```

---

### 🛠️ Build, Push, and Run Docker Image

```bash
sudo docker build -t atuljkamble/pythonhelloworld .
sudo docker images
sudo docker push atuljkamble/pythonhelloworld
sudo docker run atuljkamble/pythonhelloworld
sudo docker ps -a
```

---

## ☸️ **Kubernetes (Minikube) Setup**

> 🧠 *Kubernetes is an open-source, production-grade container orchestration system.*

### ✅ Prerequisites

* **Docker Desktop running in background**
* PowerShell run as **Administrator**

### 🍫 Install Chocolatey

Run in PowerShell (Admin):

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = `
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### 📦 Install Minikube

```powershell
choco install minikube
```

---

## 🚀 **Using Minikube & kubectl**

```bash
minikube start
minikube addons enable metrics-server
minikube dashboard  # Opens Kubernetes Dashboard in browser
```

### 🔍 Common `kubectl` Commands

```bash
kubectl get nodes
kubectl get pods
kubectl get deployments
kubectl get services
```

### 📦 Minikube Maintenance

```bash
minikube status
minikube stop
```

---

