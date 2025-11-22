# Robotics Demonstration-to-Robot Learning System
End-to-end system for capturing human demonstrations with a smart glove + cameras, converting them into unified representation vectors, training multimodal manipulation policies, and deploying them onto real robots.

This organization contains 9 repositories, each representing a distinct stage of the pipeline used in modern robotics companies (Tesla/Optimus, Figure, Boston Dynamics, Sanctuary, Google DeepMind, Toyota TRI).

---

## 🔥 High-Level Architecture

Human Demonstration → Recorder  
→ Converter  
→ Datasets  
→ Sim (Synthetic Data + Domain Randomization)  
→ Training  
→ Sim-to-Real  
→ Robot Integration (ROS2 Control Stack)  
→ Dashboard (Visualization & Debugging)  
→ Infra (Deployment + CI/CD)

Every module is cleanly separated so each team (hardware, perception, ML, simulation, robotics, DevOps) can work independently.

---

# 📦 Repository Overview

### **1. recorder/**
Capture synchronized:
- Top camera
- Wrist camera
- FSR glove data
- Timestamps  
→ Write into HDF5 files.

### **2. converter/**
Convert raw data → canonical representation vector via:
- MediaPipe hand pose
- AprilTag object pose
- FSR force calibration  
→ Save as `.npz` datasets.

### **3. datasets/**
Dataset manifests, versioning (DVC), metadata schemas, train/val/test splits.

### **4. sim/**
Simulation environments, domain randomization, synthetic representation generation using PyBullet / MuJoCo / Isaac Gym.

### **5. training/**
Model architectures, encoders, supervised BC, diffusion policies, offline RL, evaluation tools.

### **6. sim-to-real/**
Domain randomization profiles, adaptation tools, real-vs-sim divergence analysis, fine-tuning.

### **7. robot-integration/**
ROS2 nodes for real-time perception, representation builder, model inference, safety systems, robot control.

### **8. dashboard/**
React + FastAPI visualization stack for replays, dataset inspection, robot monitoring, calibration review.

### **9. infra/**
Dockerfiles, CI/CD pipelines, Kubernetes deployments, GPU cluster setup, S3 storage tooling.

---

# 🔧 Development Workflow

### **1. Collect**
Record human demonstrations using `recorder`.

### **2. Convert**
Transform the raw data into representation vectors via `converter`.

### **3. Version**
Store datasets through DVC inside `datasets`.

### **4. Simulate**
Use `sim` to generate synthetic training data with domain randomization.

### **5. Train**
Train BC / sequence / diffusion policies inside `training`.

### **6. Adapt**
Use `sim-to-real` to close reality gaps.

### **7. Deploy**
Deploy trained policies to the robot with `robot-integration`.

### **8. Visualize**
Use `dashboard` to watch replays and debug failures.

---

# 👥 Team Structure

| Team | Repo Ownership |
|------|----------------|
| Data Collection | recorder |
| Perception & Calibration | converter |
| Dataset Engineering | datasets |
| Simulation | sim |
| Machine Learning | training |
| Sim-to-Real | sim-to-real |
| Robotics / ROS2 | robot-integration |
| Tools & Visualization | dashboard |
| Infra / DevOps | infra |

---

# 📜 Licensing & Safety
This project involves:
- Real robots
- Force sensing
- High torque movements  
Follow safety protocols in `docs/SOPs/safety_sop.md`.

---

# 🌍 Contributions
Follow the org-wide **Issue & PR templates** in `.github/`.

---

# 🚀 Summary
This organization gives you a **full industrial-grade robotics learning pipeline** structured exactly like modern robotics research labs and humanoid companies.

