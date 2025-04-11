# 🔥 ThermalDetector – AI-Based Anomaly Detection in Solar PV Panels using Thermal Imagery

**Author:** Ella K.   
**Model:** YOLOv9  
**Domain:** Renewable Energy | AI | Thermal Imagin | Computer Vision

---

## 🌍 Project Overview

Photovoltaic (PV) technology plays a central role in the transition to renewable energy. Yet, many PV plants lack effective monitoring systems due to high costs and manual processes. This project aims to **automate solar panel inspection using aerial thermal imagery and deep learning**, particularly **YOLOv9** for object detection.

> **Goal:** Detect and classify different types of anomalies (e.g. hotspots, diode failures, string issues) in solar PV panels based on thermal images captured by drones.

---

## 📦 Dataset

- **Total Images:** 2723  
- **Annotated Objects:** 7772  
- **Annotation Format:** YOLOv9 (created via Roboflow)  
- **Image Size:** Resized to `640x640`  
- **Image Format:** Grayscale thermal images

### 🔄 Data Augmentations

Each original image was augmented to generate 3 versions, using:
- 50% chance of horizontal flip  
- 50% chance of vertical flip  
- Random 90° rotations (0°, 90°, 180°, 270°)  
- Random shear: ±15°  

### 🔍 Anomaly Classes

- `Single Hotspot`  
- `Multi Hotspots`  
- `Single Diode`  
- `Multi Diode`  
- `Single Bypassed Substring`  
- `Multi Bypassed Substring`  
- `String (Open Circuit)`  
- `String (Reversed Polarity)`

---

## ⚙️ Pipeline

1. **Research & Definition of Thermal Anomalies**  
2. **Data Collection & Annotation via Roboflow**  
3. **Preprocessing** – Orientation correction, resize, grayscale  
4. **Augmentation** – Diverse techniques to improve robustness  
5. **Modeling** – YOLOv9 training with evaluation metrics  
6. **Model Saving** – Export of final model (`best.pt`)  
7. **Deployment** – FastAPI/Flask-ready backend for REST inference

---

## 📊 Model Evaluation

| Metric               | Value |
|----------------------|-------|
| Precision            | 74%   |
| Recall               | 76%   |
| mAP@0.5              | 78%   |
| mAP@0.5:0.95         | 61%   |
| Fitness Score        | 63%   |

> These results show strong accuracy and reliability in detecting solar panel anomalies using thermal imagery.

---

## 🖼️ Visual Results

Sample detections from the test set:

![Sample Detection](assets/sample_detection.jpg)

---

## 🚀 How to Run

```bash
# Install requirements
pip install -r requirements.txt

# Run inference on a single image
python detect.py --weights saved_models/best.pt --source path_to_image.jpg

# Launch API server (optional)
python api_server.py
