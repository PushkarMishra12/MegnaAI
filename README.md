# 🛰️ Orbit2Ore — Autonomous Manganese Prospectivity AI Engine & UAV Exploration Platform

[![Smart India Hackathon 2026](https://img.shields.io/badge/SIH-2026-blue.svg)](https://www.sih.gov.in/)
[![Problem Statement](https://img.shields.io/badge/Problem%20Statement-SIH26009-orange.svg)](https://www.sih.gov.in/)
[![Authority](https://img.shields.io/badge/Authority-MOIL%20Limited%20%2F%20Ministry%20of%20Steel-darkgreen.svg)](https://www.moil.nic.in/)
[![Python](https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12%20%7C%203.14-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688.svg)](https://fastapi.tiangolo.com/)
[![Security Grade](https://img.shields.io/badge/Cybersecurity%20Audit-Grade%20A%2B%20(100%25)-brightgreen.svg)](#-cybersecurity--governance)
[![UAV Status](https://img.shields.io/badge/Active%20Drones-0%20Units%20(Standby%20Testbed)-yellow.svg)](#-autonomous-uav-subsystem)

---

## 🎥 System Demonstration & Walkthrough

<div align="center">
  <a href="https://youtu.be/N29ouggEJEQ" target="_blank">
    <img src="https://img.youtube.com/vi/N29ouggEJEQ/maxresdefault.jpg" alt="Orbit2Ore / MegnaAI System Demonstration" width="100%" style="border-radius: 10px; box-shadow: 0 8px 24px rgba(0,0,0,0.35); border: 1px solid #334155;">
  </a>
  <p style="margin-top: 10px;">
    <b><a href="https://youtu.be/N29ouggEJEQ" target="_blank">▶️ Click Here to Watch the Full Platform Demonstration Video on YouTube</a></b>
  </p>
</div>

---

## 📖 Executive Summary

**Orbit2Ore** is an enterprise-grade mineral intelligence and autonomous exploration platform developed for **MOIL Limited** under the **Ministry of Steel, Government of India** for **Smart India Hackathon 2026 (Problem Statement SIH26009)**.

Traditional manganese prospecting relies heavily on slow, labor-intensive manual pitting, trenching, and disjointed geological surveys. **Orbit2Ore** transforms this paradigm by unifying orbital multi-spectral satellite telemetry (Sentinel-2, Landsat-9) with UAV-borne magnetics, hyperspectral VNIR-SWIR imagery, and 3D LiDAR point cloud elevations into a unified AI discovery engine.

Through a dual-model Machine Learning pipeline, physics-calibrated multi-sensor fusion, and a closed-loop laboratory assay feedback mechanism, Orbit2Ore enables exploration geologists and mine managers to identify deep or concealed manganese ore strike corridors with sub-kilometer precision.

---

## 🌟 Core System Highlights

### 1. 📐 Multi-Sensor Drone Fusion — Exploration Priority Score (EPS)
A deterministic multi-sensor fusion algorithm calibrated against real geological priors:
$$\text{EPS} = 0.30 \cdot \text{Satellite} + 0.25 \cdot \text{Magnetometer} + 0.25 \cdot \text{Hyperspectral} + 0.20 \cdot \text{LiDAR}$$
- **High Tier ($\text{EPS} \ge 75$):** Immediate priority for confirmatory core drilling.
- **Medium Tier ($50 \le \text{EPS} < 75$):** Recommended for targeted UAV sensor sweeps.
- **Low Tier ($\text{EPS} < 50$):** Reconnaissance screened; retained in watch registry.

### 2. 🤖 Dual-Model Machine Learning Intelligence
- **Model 1 (`ProductionRiskEngine`):** `RandomForestRegressor` predicting operational risk scores (0–100) and tonnage shortfalls based on equipment availability, precipitation, shovel deployment, haul truck count, and blasting rounds.
- **Model 2 (`ManganeseDiscoveryModel`):** High-dimensional `RandomForestClassifier` trained on 1,200 observation vectors across 8 physical dimensions (SWIR Mn-Oxide Index, Ferrous Iron ratio, Thermal LST anomaly, Magnetic flux anomaly, fault proximity, terrain slope, elevation, NDVI).

### 3. 🛰️ YOLOv8 Aerial Drone Computer Vision & Continuous Learning
- **YOLOv8 Mineral Detector (`yolo_mineral_engine.py`):** High-speed, lightweight PyTorch-based anchor-free convolutional detector equipped with CSPDarknet feature extractor, Spatial Pyramid Pooling Fast (SPPF), and decoupled regression & classification heads.
- **5 Petrological Mineral Classes:**
  1. `Mn-Braunite Outcrop` (Class 0, >42% Mn grade, high economic ore)
  2. `Pyrolusite Gossan` (Class 1, 32–44% Mn grade, oxidized porous crust)
  3. `Gondite Host Rock` (Class 2, 14–26% Mn grade, manganiferous metasediment)
  4. `Structural Shear Fracture` (Class 3, mineralized fault strike veinlet)
  5. `Barren Country Rock` (Class 4, <4% Mn grade, quartzite/schist/soil background)
- **Continuous Learning & Model Training Console:** Tracks live model evolution with 4 interactive Plotly charts:
  - Dual Training Loss Trajectories (CIoU/Bounding Box + Focal Classification Loss)
  - Detection Accuracy & mAP Progression (mAP@0.5 and mAP@0.5:0.95 across epochs)
  - Multiclass Precision-Recall (PR) Curves per mineral class
  - 5×5 Normalized Confusion Matrix Heatmap
- **Drone Vision HUD Viewport:** Interactive aerial scanner featuring synthetic UAV multispectral imagery, dynamic bounding box annotations, confidence/IoU sliders, and automated reserve/grade calculation.

### 4. 🌐 Regional 2D Grid Scanner
Generates an on-demand coordinate lattice around any mine site or coordinates, executing instantaneous matrix inference to detect prospective manganese anomalies and estimate reserves using physical volumetric modeling:
$$\text{Estimated Reserve (kt)} = \frac{\text{Area (m}^2\text{)} \times \text{Thickness (m)} \times \text{Specific Gravity (4.25 t/m}^3\text{)}}{1,000}$$

### 5. 🔄 Closed-Loop Ground-Truth Feedback
When geologists log laboratory borehole assays (XRF Mn%, Fe%, $\text{SiO}_2$), the platform dynamically recalculates the parent target's average grade, elevates status to `Ground Truthed`, and boosts the target's EPS priority by +5 points.

### 6. 🗺️ Geospatial Information System (GIS) & 3D LiDAR
Interactive Folium and Leaflet.js mapping with three basemaps (Esri World Imagery, Esri Dark Gray Canvas, OpenStreetMap), four analytical heatmaps (AI Prospectivity, Thermal LST, SWIR MOI, Magnetic dipole), and Plotly 3D digital elevation models (DEMs).

### 7. 🛸 UAV Hardware Gateway & Companion Uplink
Decoupled hardware abstraction supporting REST/HTTPS, WebSocket, MQTT v5, and MAVLink v2. Compatible with Pixhawk / PX4 / ArduPilot autopilots via an onboard companion computer bridge (`companion_drone_uplink.py`).
> **Operational Status Constraint:** The platform defaults to **0 Active Drones / Standby / Simulation Testbed** unless verified physical hardware is explicitly connected via the hardware gateway.

### 8. 🔐 Military-Grade RBAC & 3-Tier Governance
Comprehensive 6-persona RBAC matrix (Admin, Team Lead, Geologist, UAV Operator, Mining Dispatcher, Field Tech) with PBKDF2-HMAC-SHA256 password hashing (100,000 iterations, 16-byte random salts), constant-time comparisons, and Team Lead elevation workflows.

---

## 🏗️ Architecture & Component Topology

```
┌────────────────────────────────────────────────────────────────────────┐
│                      GLASSMORPHIC SPA FRONTEND                         │
│   (HTML5 • Vanilla CSS Tokens • ES Modules • Leaflet.js • Plotly.js)   │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ HTTP / REST & Static Assets
┌───────────────────────────────────▼────────────────────────────────────┐
│                       FASTAPI REST API SERVER                          │
│     Authentication • Session Auth • CORS Middleware • Static Mount     │
└───────┬──────────────┬──────────────┬──────────────┬─────────────┬─────┘
        │              │              │              │             │
┌───────▼──────┐┌──────▼──────┐┌──────▼──────┐┌──────▼──────┐┌─────▼─────┐
│  AI/ML CORE  ││  GIS ENGINE ││  SECURITY   ││ UAV GATEWAY ││ COMPANION │
│  YOLOv8 CNN  ││  Folium Map ││  PBKDF2/Salt││ REST/MAVLink││ Drone U/L │
│  RF Regress  ││  Plotly 3D  ││  RBAC/Audit ││ Hardware Ab ││ Telemetry │
│  RF Classif  ││ Spectral/Mag││  TL Inboxes ││ Telemetry   ││ MAVLink v2│
└───────┬──────┘└─────────────┘└──────┬──────┘└─────────────┘└───────────┘
        │                             │
┌───────▼─────────────────────────────▼──────────────────────────────────┐
│                      SQLite PERSISTENCE LAYER                          │
│               mangan_ai.db (Write-Ahead Logging Mode)                  │
│   targets • assays • ops_logs • users • permissions • requests • audit │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository File Map

| File | Size | Role & Architectural Purpose |
|:---|:---:|:---|
| [`api_server.py`](api_server.py) | 55 KB | FastAPI REST API Server — routes, endpoints, JSON responses, SPA static hosting |
| [`yolo_mineral_engine.py`](yolo_mineral_engine.py) | 20 KB | YOLOv8 Petrological Computer Vision Engine & Continuous Learning Trainer |
| [`static/`](static/) | Directory | Modern Glassmorphic SPA Frontend — HTML5, CSS3, ES modules, Leaflet, Plotly |
| [`orbit2ore_engine.py`](orbit2ore_engine.py) | 57 KB | Core AI/ML Engine — data seeding, EPS fusion, Random Forest, grid scanner |
| [`security_engine.py`](security_engine.py) | 68 KB | Security, RBAC, Auth, TL Governance, Audit Trail |
| [`gis_engine.py`](gis_engine.py) | 21 KB | Folium GIS Map, Plotly 3D LiDAR, Spectral & Magnetic charts |
| [`drone_backend_adapter.py`](drone_backend_adapter.py) | 11 KB | UAV Fleet Manager, Hardware Gateway Abstraction |
| [`companion_drone_uplink.py`](companion_drone_uplink.py) | 11 KB | UAV Onboard Companion Bridge — MAVLink/Serial live telemetry uplink |
| [`cybersecurity_audit.py`](cybersecurity_audit.py) | 21 KB | Comprehensive 19-probe OWASP/NIST audit calibration suite |
| [`start_server.bat`](start_server.bat) | 400 B | Windows startup batch script launching Uvicorn on port 8000 |
| [`codebase_architecture.md`](codebase_architecture.md) | 26 KB | In-depth technical architecture blueprint & database schemas |

---

## 🧪 Verification & Security Audit

The codebase includes an automated audit suite validating cryptographic security and regulatory compliance:

```bash
# OWASP & NIST Cybersecurity Audit (19 Probes)
python cybersecurity_audit.py
```

---

## 🛡️ Cybersecurity & Governance

Orbit2Ore enforces strict digital identity and access controls audited against **OWASP Top 10 (2021)** and **NIST SP 800-63B**:
- **PBKDF2-HMAC-SHA256:** 100,000 iterations with unique 16-byte random salts.
- **Timing Attack Resistance:** Constant-time hash comparisons via `hmac.compare_digest()`.
- **Brute-Force Rate Limiting:** Account lockout for 15 minutes after 5 failed attempts.
- **Injection Sanitization:** Full parameterization across all SQL queries and HTML output encoding.
- **Forensic Audit Logging:** Immutable chronological audit trail in SQLite.
- **Certified Audit Score:** **19/19 probes passed (100.0%, Grade A+ Exemplary)**.

---

## 📜 Official Compliance & Attribution

- **Competition:** Smart India Hackathon (SIH) 2026
- **Problem Statement ID:** SIH26009
- **Target Organization:** MOIL Limited / Ministry of Steel, Government of India
- **Primary Mining Belts:** Sausar Group (Balaghat, Dongri Buzurg, Gumgaon, Mansar, Tirodi, Chikla), Dharwar Craton, Eastern Ghats
- **Security & Data Sanitization:** Strictly sanitized for public version control; zero credentials or private keys committed.
