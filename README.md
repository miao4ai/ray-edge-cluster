# ray-edge-cluster
Ray Edge Cluster — Distributed Edge AI Framework for Raspberry Pi and Jetson

## 🌍 Overview
**Ray Edge Cluster** is a lightweight distributed computing framework designed for **Edge AI** scenarios — running across **Raspberry Pi clusters**, **Jetson Orin Nano**, or any other ARM-based devices.  
It leverages [Ray](https://www.ray.io) for unified task scheduling, actor management, and resource-aware distributed execution.

Typical use cases:
- Distributed image / sensor data preprocessing on Raspberry Pi nodes  
- GPU-accelerated inference on Jetson Orin Nano  
- Federated or collaborative model training at the edge  
- Edge → Cloud pipeline synchronization (via Ray Serve)

---

## 🧩 Architecture

Ray Edge Cluster adopts a hybrid edge computing architecture —  
where Raspberry Pi nodes handle CPU-side data preprocessing and orchestration,  
while Jetson Orin Nano provides GPU acceleration for inference or training.

```text
                        ┌─────────────────────────────────────────┐
                        │             Edge Cluster Head            │
                        │        Raspberry Pi 5 (16GB RAM)         │
                        │------------------------------------------│
                        │ • Ray Head Node (Scheduler & Dashboard)  │
                        │ • Task Orchestration & Monitoring        │
                        │ • Log Collection / Aggregation           │
                        └─────────────────────────────────────────┘
                                       │   Gigabit LAN
             ┌──────────────────────────┴──────────────────────────┐
             │                                                     │
┌────────────────────────────┐                       ┌────────────────────────────┐
│ Raspberry Pi Worker Nodes  │                       │ Jetson Orin Nano 8GB Node │
│ (CPU-based Edge Devices)   │                       │ (GPU-Accelerated Node)    │
│----------------------------│                       │----------------------------│
│ • Data Preprocessing       │                       │ • Deep Inference / Training│
│ • ETL / Sensor Fusion      │                       │ • CUDA / TensorRT Runtime  │
│ • Lightweight Ray Tasks    │                       │ • Model Serving (Ray Serve)│
└────────────────────────────┘                       └────────────────────────────┘
             │                                                     │
             └──────────────────────────┬──────────────────────────┘
                                        │
                        ┌─────────────────────────────────────────┐
                        │           Optional Cloud Sync            │
                        │      (e.g., MLflow / S3 / BigQuery)      │
                        └─────────────────────────────────────────┘
```
