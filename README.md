# 🦷 Dentris AI — AI-Powered Dental Analysis

**Dentris AI** is an AI-powered dental analysis platform designed to assist with the identification and visualization of potential dental conditions from intraoral photographs. It combines computer vision, deep learning, and an AI-powered assistant to make dental image analysis more accessible and understandable.

The platform aims to support preliminary dental screening by identifying potential findings, displaying relevant visual evidence, and presenting structured results through an intuitive web interface.

> **Disclaimer:** Dentris AI is a research and decision-support prototype, not a substitute for professional dental examination, clinical diagnosis, or treatment advice.

---

## ✨ Key Features

- **AI-Powered Dental Image Analysis** — Analyzes intraoral dental photographs using trained computer vision models.
- **Object Detection** — Identifies and localizes potential dental findings using bounding boxes.
- **Dental Image Classification** — Classifies image content into supported dental categories.
- **Visual Results** — Presents detected regions and model predictions through the web interface.
- **AI Dental Assistant** — Uses a locally hosted language model to explain structured analysis results.
- **Browser-Based Interface** — Provides an interactive experience for uploading images and viewing results.
- **Local AI Inference** — Supports browser-based inference and backend processing, depending on the configured model.
- **Modular Architecture** — Separates the frontend, inference services, and assistant components.

## 🧠 AI Models

Dentris AI uses a modular computer vision pipeline with models designed for different tasks.

| Model | Purpose |
|---|---|
| YOLOv8 Nano | Object detection and localization |
| SigLIP Dental Classifier | Image classification using visual representations |
| ConvNeXt-Tiny | Dental image classification |
| Qwen2.5-3B | Local language-model assistant for explaining structured findings |

### Model Pipeline

1. The user uploads an intraoral photograph.
2. The application validates and preprocesses the image.
3. The configured computer vision model analyzes the image.
4. Predictions and confidence scores are processed using application-level thresholds.
5. Supported detections and classifications are displayed in the interface.
6. The local AI assistant can explain the structured findings returned by the analysis pipeline.

**Important:** The supported classes, model checkpoints, inference thresholds, and deployment configuration depend on the selected model. The application should not interpret a missing detection as proof that a tooth is healthy.

## 🛠️ Technology Stack

### Frontend
- React 19
- TanStack Start
- Tailwind CSS

### Artificial Intelligence
- YOLOv8
- SigLIP
- ConvNeXt-Tiny
- PyTorch
- ONNX Runtime Web
- WebAssembly (WASM)

### Backend
- Python
- FastAPI

### Local Language Model
- Qwen2.5-3B
- Ollama

### Development and Deployment
- Git and GitHub
- Node.js
- Python virtual environments
- GPU-accelerated training and inference, where supported

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      User            │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  React Web Interface │
                    │  Image Upload & UI    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Image Preprocessing  │
                    │ Validation & Resizing│
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  Dental AI Pipeline  │
                    │ Detection / Classify │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Structured Findings  │
                    │ Labels & Confidence  │
                    └──────────┬───────────┘
                               │
                    ┌──────────┴───────────┐
                    ▼                      ▼
          ┌──────────────────┐   ┌──────────────────┐
          │ Results & Visuals│   │ Qwen2.5 Assistant│
          │ in Web Interface │   │ Local Explanations│
          └──────────────────┘   └
