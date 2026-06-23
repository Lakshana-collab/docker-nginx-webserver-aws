# Dockerized Nginx Web Server Deployment on AWS EC2

## Project Overview

This project demonstrates the deployment of an Nginx web server inside a Docker container on an Ubuntu-based AWS EC2 instance.

The objective was to understand Docker containerization, container lifecycle management, web server deployment, monitoring, and troubleshooting in a cloud environment.

## Technologies Used

* Docker
* Nginx
* AWS EC2
* Ubuntu Linux
* HTML

## Steps Performed

### 1. Docker Installation

Installed Docker on an Ubuntu EC2 instance and verified the installation.

```bash
sudo apt update
sudo apt install docker.io -y
```

### 2. Pull Nginx Image

```bash
sudo docker pull nginx
```

### 3. Run Nginx Container

```bash
sudo docker run -d --name my-webserver -p 80:80 nginx
```

### 4. Verify Container Status

```bash
sudo docker ps
```

### 5. Deploy Custom Web Page

Created a custom HTML page and mounted it into the Nginx container using Docker volumes.

```bash
sudo docker run -d --name custom-web -p 80:80 -v $(pwd)/index.html:/usr/share/nginx/html/index.html nginx
```

### 6. Configure AWS Security Group

Allowed inbound HTTP traffic on port 80 to make the web server accessible from the internet.

## Challenges Faced

### Incorrect Image Name

Initially used `ngnix` instead of `nginx`, which resulted in an image pull error.

### Port Mapping Confusion

The container was first exposed on port 8080, requiring access through `EC2_PUBLIC_IP:8080`.

### Security Group Configuration

Learned that Docker port mapping alone is insufficient without proper AWS Security Group rules.

### HTTP vs HTTPS

Observed browser security warnings and learned the difference between HTTP and HTTPS.

## Key Learnings

* Docker image and container management
* Container lifecycle operations
* Port mapping concepts
* Docker volume mounting
* AWS Security Group configuration
* Basic troubleshooting using Docker logs and status commands

## Outcome

Successfully deployed and managed a containerized Nginx web server on AWS EC2 and hosted a custom web page using Docker.
