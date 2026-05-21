# 🍞 MoldyBread AI: Edge-Native Moldy Bread Detection

![ONNX Runtime](https://img.shields.io/badge/ONNX_Runtime-WebAssembly-blue?style=for-the-badge&logo=onnx)
![YOLO11n](https://img.shields.io/badge/Model-YOLO11n-00FFFF?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

MoldyBread AI is a zero-latency, fully client-side computer vision system designed to detect moldy or spoiled bread in real time. By leveraging WebAssembly (WASM) and ONNX Runtime Web, this system runs a YOLO11n object detection model directly inside the browser—without requiring cloud servers, APIs, or backend processing.

> 💡 Note: This project was built as an educational implementation of edge-native AI deployment using only HTML, CSS, JavaScript, and an ONNX model.

---

# ✨ Core Features

## 🍞 Real-Time Mold Detection
Detects moldy bread directly from webcam or uploaded images using a YOLO11n ONNX model running entirely in-browser.

## ⚡ Edge-Native Inference
All inference runs locally on the user's device using WebAssembly, ensuring:
- Zero server latency
- Better privacy
- No internet dependency after loading

## 📸 Smart Snapshot Logging
Automatically captures detection frames using HTML5 Canvas for visual logging and monitoring.


## 📐 Auto Coordinate Scaling
Automatically converts normalized YOLO output coordinates into accurate screen-space bounding boxes for perfect overlay alignment.

---

# 🧠 Model Architecture & Training

This project uses a lightweight **YOLO11 Nano (YOLO11n)** architecture optimized for browser-based inference.

The model is designed to balance:
- High detection accuracy
- Low computational cost
- Fast real-time inference on low-end hardware

---

# 📊 Dataset

The model was trained using a custom Moldy Bread Detection dataset containing multiple bread conditions such as:
🔗 **[View the Dataset on Roboflow Here](https://app.roboflow.com/bread-king-bad/bread-quality/1)** 
- roti_bagus(Fresh Bread)
- roti_busuk(Moldy Bread)

Dataset images were annotated and exported in YOLO format.

---

# 🚀 Training Pipeline

The training process was performed using a custom YOLO training workflow designed for rapid experimentation and deployment.

🔗 **[Access the YOLO Trainer (Google Colab)](https://colab.research.google.com/drive/1_NNXV5pG9PKC7TkE6M_a0Jxq_S4wMdCz)**
## Evaluation Metrics

| Metric | Score |
|---|---|
| Precision (P) | 0.9762  |
| Recall (R) | 0.8733 |
| mAP50 | 0.9462 |
| mAP50-95 | 0.9115 |
| F1-Score | 0.9219 |

> Metrics above are sample results and may vary depending on dataset quality and training configuration.

---

# 🛠️ System Components & Codebase Explanation

The repository is intentionally lightweight and focuses on frontend-only deployment.

---

## 1. `index.html` — Interface & Detection Viewport

Acts as the main UI structure and rendering layer.

### Features:
- Live webcam feed
- Detection overlay canvas
- Bounding box rendering
- Detection result panel
- Responsive layout using Flexbox

### Rendering Strategy
A transparent `<canvas>` is stacked directly above the `<video>` element using absolute positioning to ensure pixel-perfect bounding box alignment.

### Processor Canvas
Includes a hidden `640x640` canvas used for:
- Frame resizing
- Tensor preprocessing
- Input formatting for the ONNX model

---

## 2. `app.js` — Inference Engine

Handles the entire AI inference pipeline.

### Responsibilities:
- Camera initialization
- Frame extraction
- Tensor conversion
- Running ONNX inference
- Drawing detections
- Notification handling
- Audio alert management

### Tensor Formatting
Converts RGBA image data into Float32 NCHW tensors required by YOLO.

### Non-Maximum Suppression (NMS)
Implements custom JavaScript-based:
- IoU (Intersection over Union)
- NMS filtering

to remove overlapping bounding boxes.

### State Machine
Uses a detection state manager to prevent repeated:
- Alarm playback
- Browser notifications
- Snapshot spam

during continuous detection events.

---

# 🚀 Deployment (vercel)

Because the project only uses static assets (HTML, CSS, JS, ONNX), deployment is extremely simple.

## Steps

1. Clone or fork this repository.
2. Ensure your trained model is exported as:

```bash
best.onnx
```

3. Place the model in the root project directory.
4. Open repository settings → Pages.
5. Deploy from the `main` branch.
6. Open the generated URL.
7. Grant camera and notification permissions.
8. Start the detection system.

---

# 📁 Project Structure

```bash
project-folder/
│
├── best.onnx
├── index.html
├── style.css
├── app.js
└── README.md
```

---

# 🔥 Technologies Used

- HTML
- CSS
- JavaScript
- ONNX Runtime Web
- WebAssembly (WASM)
- YOLO11n
- HTML5 Canvas API
- Web Audio API
- Browser Notifications API

---

# 💡 Future Improvements

- Multi-class bread classification
- Real-time analytics dashboard
- Mobile optimization
- Edge TPU support
- Detection history storage
- Confidence heatmap visualization

---

# 👨‍💻 Author Team

- •dimas ardiyansyah
- •rizwan fahreza
- •reyhan nirhana
- •zaidan zia ulhaq
- •ilham nur salam

