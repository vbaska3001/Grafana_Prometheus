# Prometheus & Grafana Monitoring Setup (Helm)

This repository contains the configuration and installation steps for setting up **Prometheus** and **Grafana** on Kubernetes using **Helm**, with **Persistent Volumes (PV)** and **Persistent Volume Claims (PVC)** for data persistence.

## Repository Structure
- `Prometheus/` – Prometheus PV, PVC and related configs
- `Grafana/` – Grafana PV, PVC and Grafana manifests
- `Prometheus_Grafana_Installation/` – Text file with detailed installation steps

## Installation Order

### 1. Prometheus Installation
- Create Prometheus **PV and PVC**
- Install Prometheus using **Helm**
- Persistent storage enabled for Prometheus server and Alertmanager

```bash
helm install prometheus prometheus-community/prometheus \
--namespace monitoring \
--set alertmanager.persistentVolume.storageClass="local-storage" \
--set server.persistentVolume.storageClass="local-storage"
```

### 2. Grafana Installation
- Create Grafana **PV and PVC**
- Apply **grafana.yaml** manifest for Grafana deployment
- Grafana connects to Prometheus as the data source
- Install Grafana using **Helm**
- Persistent storage enabled for Prometheus server and Alertmanager

### Reference
A detailed step-by-step guide is available in: installation/install-steps.txt

### Notes
- Helm is used for installing and managing Prometheus (and optionally Grafana)
- PV and PVC ensure data persistence across pod restarts

## Screenshots for reference

### Grafana Dashboard Overview
<img width="500" height="500" alt="Grafana Dashboard Overview" src="https://github.com/user-attachments/assets/b12f8622-1c19-4d82-9564-fcff2c99b406" />

### Grafana K8 Cluster Dashboard 
<img width="500" height="500" alt="Grafana K8 Cluster Dashboard" src="https://github.com/user-attachments/assets/9100a16b-765c-4201-8f8e-b046cfdbdc72" />

### Grafana K8 Resource Monitor
<img width="500" height="500" alt="Grafana K8 Resource Monitor" src="https://github.com/user-attachments/assets/2b9cbe92-5dba-4a1c-860b-be7f33a5edb3" />

### Grafana K8 Resource Monitor 2
<img width="500" height="500" alt="Grafana K8 Resource Monitor 2" src="https://github.com/user-attachments/assets/0142d673-e2cc-47f3-abbb-ba098a87e007" />


