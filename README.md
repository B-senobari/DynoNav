# DynoNav
DynoNav isolates true, independent object motion from camera ego-motion in real time using epipolar geometry and SMC particle filtering to reliably detect dynamic hazards for assistive navigation.



https://github.com/user-attachments/assets/453ac329-4200-4e6a-8fec-bd2b73a1dad5



## Technical Overview

**DynoNav** is an advanced, edge-optimized computer vision framework designed to enhance spatial mobility and hazard perception during mobile navigation. When a camera is worn by a walking pedestrian or mounted on a mobile platform, the entire visual scene experiences continuous global displacement (ego-motion). Traditional feature tracking and optical flow algorithms frequently misclassify stationary background structures as dynamic obstacles due to this global visual motion.

**DynoNav** solves this challenge by decoupling optical displacement caused by camera kinematics (translation and rotation) from true, independently moving hazards in the environment. By combining geometry-based ego-motion recovery, epipolar constraint verification, and Sequential Monte Carlo (SMC) particle filtering, the framework provides robust, real-time tracking of real dynamic threats in mobile navigation scenarios.

*Current Status: This repository contains the initial preview version. The project is actively under development, focusing on optimizing edge execution latency and dynamic tracking stability.*


---

## Key Features

* **Camera Ego-Motion Separation:** Isolates background features by dynamically masking active foreground object tracks to recover rotation ($R$) and translation ($t$) camera pose matrices using RANSAC-supported Essential matrix ($E$) estimation.
* **DynoSAM (We were inspired by this project) Independent Motion Separation:** Verifies feature dynamics against epipolar geometry constraints to detect entities violating global background camera motion models, assigning a precise dynamic `moving_score`.
* **SMC Particle Filtering:** Utilizes a 6D continuous state vector tracking model ($[c_x, c_y, w, h, v_x, v_y]^T$) with systematic resampling and adaptive noise scaling to prevent tracking loss during rapid camera panning or walking vibrations.
* **Monocular Proximity Estimation:** Incorporates normalized depth map estimation to categorize dynamic hazards into spatial proximity bands (*Near*, *Very Near*).
---

## Academic Context & Credits
<img width="4080" height="3060" alt="MVIMG_20260710_133346" src="https://github.com/user-attachments/assets/b234ef45-0f56-49c2-8c5d-8a8025ac1a7d" />

This project is developed as part of research conducted at the **Human-Computer Interaction & Multimodal Interfaces Lab (HUM-HI Lab)**.

* **Laboratory:** HuM-HI Lab (Human Machine Laboratory - Hybrid Intelligence)
* **Institution:** University of Messina (UniME), Italy
* **Supervisor:** Prof. Giancarlo Iannizzotto
* **Author:** Benyamin Senobari

---

## Getting Started (Initial Preview)

### Prerequisites

* Python 3.9 or higher
* OpenCV with C++ / CUDA acceleration support (recommended)
* BLE-compatible hardware (optional, for haptic modules)

### Setup

1. **Clone the repository:**
```bash
git clone https://github.com/B-Senobari/DynoNav.git
cd DynoNav

```


2. **Install dependencies:**
```bash
pip install -r requirements.txt
