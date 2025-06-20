
# 📊 Grafana Reporting and Alerting – DevOps Project

A complete real-time system monitoring and alerting solution built using **Prometheus**, **Node Exporter**, and **Grafana** on an Ubuntu virtual machine. This project allows you to collect system performance metrics like CPU and memory usage, visualize them in interactive dashboards, and configure alert notifications using Alertmanager and Email.

---

## 📄 Abstract

This project focuses on building a lightweight and terminal-based monitoring setup without containerization. **Prometheus** collects time-series data from an Ubuntu VM using **Node Exporter**. **Grafana** connects to Prometheus and displays the metrics using real-time dashboards. Alert rules are configured in Grafana to notify users via **Alertmanager** and **Email** when thresholds are breached (e.g., CPU usage > 80%). All configurations are managed through YAML and Nano text editor for simplicity and accessibility.

---

## 📌 Scope and Objectives

### 🔍 Scope

- Real-time monitoring of system metrics (CPU, memory, disk)
- Data visualization through Grafana dashboards
- Configured using a simple and lightweight terminal setup
- Alert integration for proactive issue detection

### ✅ Objectives

- Install and configure **Prometheus**, **Grafana**, and **Node Exporter**
- Visualize collected metrics in **Grafana**
- Configure alert rules with **Alertmanager** and email notifications
- Manage services using **Systemd**
- Edit YAML configuration files using the **Nano** text editor

---

## 🛠️ System Requirements

### 🔧 Hardware Requirements

- System with minimum 4 GB RAM
- Linux-based or Windows system with WSL
- Internet connection for installation

### 💻 Software Requirements

- Prometheus
- Grafana
- Node Exporter
- Nano (text editor)
- Web Browser (Chrome/Firefox)
- Slack/Email (for optional alert notifications)
- Terminal (CLI)

---

## 🧱 Project Design Overview

1. **Node Exporter** installed to expose system metrics on the Ubuntu VM.
2. **Prometheus** scrapes these metrics at regular intervals.
3. **Grafana** connects to Prometheus as a data source.
4. **Grafana Dashboards** visualize CPU, memory, and disk usage.
5. **Alert Rules** are set to notify users when thresholds are met.
6. **Systemd Services** ensure continuous background operation.
7. **YAML files** are used to manage configuration.
8. **Nano Editor** is used to perform quick file edits in the terminal.

---

## 🧪 Step-by-Step Installation & Commands

### 1. Install Prometheus
```bash
sudo apt update
sudo apt install prometheus
sudo systemctl start prometheus
sudo systemctl enable prometheus
,,,

### 2. Install Grafana
```bash
sudo apt-get install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server


### 3. Install Node Exporter
```bash
tar -xvf node_exporter-*.tar.gz
sudo mv node_exporter-*/node_exporter /usr/local/bin/
nohup /usr/local/bin/node_exporter

### 4. Configure Prometheus to Scrape Node Exporter
```bash
sudo nano /etc/prometheus/prometheus.yml

### Add:
```bash
yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']

### Restart Prometheus:
```bash
sudo systemctl restart prometheus

### 5. Set Up Grafana Dashboard
Open: http://localhost:3000

Login: admin / admin

Add Prometheus as data source:
Configuration → Data Sources → Add → Prometheus
Set URL: http://localhost:9090

### 🚨 Alert Configuration
Alerts created in Grafana Alerting > Alert Rules

Contact points added under Alerting > Contact Points

Notification sent to:

Alertmanager

Email (vedhavithya10@gmail.com)

### ✅ Conclusion
This project demonstrates how to integrate Prometheus and Grafana to monitor system performance metrics and alert users in real time. It highlights how a simple setup using open-source tools can create a powerful and efficient monitoring system with email-based alerting.

### 🔮 Future Enhancements
> Add monitoring for multiple systems or nodes

> Integrate advanced alert channels (e.g., Teams, Opsgenie)

> Enable role-based access control (RBAC) in Grafana

> Extend monitoring to cloud infrastructure

> Incorporate anomaly detection using ML
