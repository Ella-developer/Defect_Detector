# ThermalDetector – AI-Powered Anomaly Detection in Solar PV Panels using Thermal Imagery

**Author:** Ella K.  
**API Developer:** Ella K. 
**Model:** YOLOv9  
**Domain:** Renewable Energy | AI | Thermal Imaging | Computer Vision | FastAPI

---

## 🌍 Project Overview

Photovoltaic (PV) systems are crucial in the global clean energy transition. However, the lack of real-time, low-cost, and automated inspection solutions still affects the performance of many PV sites. This project introduces a complete AI-based pipeline to **automatically detect thermal anomalies in solar panels using YOLOv9**, deployed via a RESTful API with FastAPI and Docker.

> **Objective:** Automatically classify 8 types of thermal defects in solar modules using annotated drone-captured grayscale images.

---

## 📦 Dataset

- **Original Images:** 2723  
- **Augmented Samples:** ~7500  
- **Total Objects:** 7772  
- **Annotation Format:** YOLOv9 (via Roboflow)  
- **Image Size:** 640×640  
- **Image Format:** Grayscale

### 🔄 Data Augmentations

- Horizontal / vertical flips (50%)  
- Random 90° rotations  
- Random shear: ±15°  
- Hue, brightness, exposure: ±15°  

### 🧪 Anomaly Classes

- `Single Hotspot`  
- `Multi Hotspots`  
- `Single Diode`  
- `Multi Diode`  
- `Single Bypassed Substring`  
- `Multi Bypassed Substring`  
- `String (Open Circuit)`  
- `String (Reversed Polarity)`

---

## ⚙️ Pipeline Overview

1. Thermal anomaly research & taxonomy  
2. Data collection & annotation via Roboflow  
3. Preprocessing (resize, orientation, grayscale)  
4. Data augmentation  
5. YOLOv9 training and evaluation  
6. Inference-ready export (`Th_G_v9.pt`)  
7. API deployment using FastAPI & Docker  


> YOLOv9 achieved robust performance on unseen thermal test images.

---

## 🧠 API Overview (FastAPI)

**Endpoint:** `POST /predict/`  
**Input:** Thermal image (form-data)  
**Output:**  
- 🖼️ JPEG image with bounding boxes  
- 📦 `X-Anomaly-Count` and `X-Detection-Result` in headers

### 🔁 Example Request (curl)

```bash
curl -X POST "http://localhost:8000/predict/" \
  -H  "accept: image/jpeg" \
  -F "file=@sample.jpg" \
  --output result.jpg
```

Or use the auto-generated docs at:

> 🔗 http://localhost:8000/docs

---

## 🐳 Dockerized Deployment

### 🔧 Build & Run:

```bash
# Build Docker image
docker build -t solar-api .

# Run container
docker run -p 8000:8000 solar-api
```

### 📦 Or use Docker Compose:

```bash
docker-compose up --build
```

---

## 📁 Project Structure

```
solar-anomaly-api/
├── api.py
├── predictor.py
├── model_loader.py
├── Th_G_v9.pt
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## 👨‍💻 Developers

- **ML Engineer:** Ella K.  

---

## 📜 License

MIT License — Free for academic and commercial use with attribution.
```
