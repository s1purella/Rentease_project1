# Monitoring GitHub Actions with Prometheus and Grafana

This serves as project 2, a continuation of project 1, which is the base project. 
It demonstrates how to monitor GitHub Actions workflows using 
**Prometheus, Grafana, and the github-actions-exporter.** 

## Benefits
The goal is to visualize key CI/CD metrics like:

1. Build Duration
2. Failure rates
3. Test coverage


Reporting, visualizing, and monitoring are ideal for DevOps engineers, SREs, and security professionals 
looking to enhance visibility over CI/CD performance. It gives you a quick view to carry out your
gap analysis better in optimizing your workflow. Let's jump right into it.

 ## **Architecture Overview**
 Here's a high-level architecture diagram of the setup
![GitHub Actions](screenshots/Monitoring%20CICD%20Architecture%20with%20prometheus%20and%20Grafana.png)

## Prerequisites
1. GitHub repository with existing workflows
2. Access to a server to run Prometheus, Grafana, and GitHub Actions Exporter

 ## Step-by-step Guide

Install Docker Compose 
```bash 
sudo apt update
sudo apt install -y docker.io docker-compose
sudo usermod -aG docker $USER
newgrp docker  # Refresh group permissions
```

**Verify**
```bash
docker --version && docker-compose --version
```
***Create the folder*** `monitoring` with two files `docker-compose.yml` and  prometheus.yml in it

`docker-compose.yml` configuration code
```bash
version: '3.8'  # Add this line at the top
services:
  prometheus:
    image: prom/prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    restart: unless-stopped

  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
    volumes:
      - grafana-storage:/var/lib/grafana
    restart: unless-stopped

```

`prometheus.yml` configuration below:
```bash
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

```
***Start the services***
```bash
cd ~/monitoring
docker-compose up -d
```

***Install GitHub Exporter***
We'll use ghcr.io/labbs/github-actions-exporter image
Create another folder with a configuration file `/github-exporter/config.yaml`

```bash
github:
  token: "ghp_yourNewTokenHere"  # Create at: https://github.com/settings/tokens (repo + admin:org scopes)
  repos:
    - owner: "jozzyjcon"
      name: "Rentease_project1"
```
***Now update your docker-compose.yml***
```bash

  github-exporter:  # Properly indented under services
    image: ghcr.io/labbs/github-actions-exporter:latest
    ports:
      - "9999:9999"
    volumes:
      - /home/ubuntu/monitoring/github-exporter/config.yaml:/config.yaml  # Full absolute path
    restart: unless-stopped
```
