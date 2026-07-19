# 🍎 AI Nutritionist

> Full-Stack AI Platform for Intelligent Food Photo Analysis & Nutrition Management

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?logo=python&logoColor=white)](https://python.org)
[![Django](https://img.shields.io/badge/Django-4.0+-092E20?logo=django&logoColor=white)](https://www.djangoproject.com/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-seg-111F4D?logo=ultralytics&logoColor=white)](https://ultralytics.com/)
[![Render](https://img.shields.io/badge/Deployed%20on-Render-46E3B7?logo=render&logoColor=white)](https://render.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**🚀 Live Demo:** [ai-nutritionist-lsha.onrender.com](https://ai-nutritionist-lsha.onrender.com)

---

## 📸 Screenshots

### 🏠 Home Page
![Home](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/home.png)

### 🔐 Login Page
![Login](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/login.png)

### 👤 User Dashboard
![User Dashboard](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/userdash.png)

### 🤖 AI Food Segmentation
![AI Segmentation](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/AI%20seg.png)

### 🥗 Nutritionist Dashboard - Consultations
![Nutridash Consultations](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/nutridash%20cons.png)

### 📋 Nutritionist Dashboard - Diet Plans
![Nutridash Dietplan](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/nutridash%20dietplan.png)

### 📅 User Book Consultation
![User Book Consultation](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/user%20book%20cons.png)

---

## ✨ Features

### 🔥 Core AI Features
- 📸 **AI Food Photo Analysis** — Upload a food photo, YOLOv8-seg identifies and segments each food item
- 🎯 **Instance Segmentation** — Individual bounding boxes and masks for each food item
- 📊 **Calorie Estimation** — Automatic nutritional calculation per detected item
- ⚡ **Real-Time Processing** — Sub-second inference on optimized CPU deployment

### 🏥 Platform Features
- 👤 **Multi-Role System** — Patients, Nutritionists, and Admins
- 📅 **Consultation Booking** — Patients book appointments with nutritionists
- 📋 **Diet Plan Management** — Nutritionists create personalized diet plans
- 💳 **Payment Integration** — Secure payment processing for consultations
- 📱 **Responsive Design** — Works on desktop, tablet, and mobile

### 🛠 Technical Features
- 🔄 **RESTful API** — Clean, documented Django REST Framework endpoints
- 🔐 **Authentication** — Secure user registration, login, and role-based access
- 📦 **Database** — SQLite3 with optimized schema for users, consultations, diet plans, and meal history
- 🚀 **CI/CD Pipeline** — Automated deployment via GitHub Actions
- ☁️ **Cloud Deployed** — Live on Render with environment configuration

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Computer Vision** | YOLOv8-seg (Ultralytics), PyTorch |
| **Backend** | Django 4.0+, Django REST Framework |
| **Database** | SQLite3 |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Payment** | Integrated payment gateway |
| **Deployment** | Render (Web Service) |
| **CI/CD** | GitHub Actions |
| **AI Tools** | Cursor, GitHub Copilot |
| **Version Control** | Git, GitHub |

---

## 🏗 Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Client        │────▶│   Django REST   │────▶│   YOLOv8-seg    │
│   (Browser)     │◀────│   API           │◀────│   Model         │
│                 │     │                 │     │                 │
│ • Upload Photo  │     │ • Image Upload  │     │ • Instance      │
│ • Book Consult  │     │ • Inference     │     │   Segmentation  │
│ • View Dietplan │     │ • Calorie Calc  │     │ • Classify      │
│ • Payment       │     │ • Auth/Roles    │     │                 │
└─────────────────┘     └─────────────────┘     └─────────────────┘
         │                       │                       │
         │              ┌────────┴────────┐               │
         │              │   SQLite3 DB      │               │
         │              │                   │               │
         │              │ • Users (Patient/ │               │
         │              │   Nutritionist/   │               │
         │              │   Admin)          │               │
         │              │ • Consultations   │               │
         │              │ • Diet Plans      │               │
         └──────────────│ • Meal History    │───────────────┘
                        │ • Payments        │
                        └───────────────────┘
```

---

## 🚀 Installation

### Prerequisites
- Python 3.9+
- pip
- Git

### Clone Repository

```bash
git clone https://github.com/ramdaninourhane26-hash/pfe.git
cd pfe
```

### Create Virtual Environment

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Database Setup

```bash
python manage.py migrate
python manage.py createsuperuser
```

### Run Development Server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000`

---

## 💻 Usage

### For Patients
1. Register as a patient
2. Upload food photos for AI analysis
3. Book consultations with nutritionists
4. View personalized diet plans
5. Make payments securely

### For Nutritionists
1. Register as a nutritionist
2. Manage consultation requests
3. Create personalized diet plans
4. Track patient progress

### For Admins
1. Access admin dashboard
2. Manage users and roles
3. Monitor platform activity

---

## 🧠 AI Model

### YOLOv8-seg Configuration

```python
from ultralytics import YOLO

# Load pretrained YOLOv8-seg
model = YOLO('yolov8n-seg.pt')

# Train on custom food dataset
model.train(
    data='data/food_dataset.yaml',
    epochs=100,
    imgsz=640,
    batch=16,
    device='cpu',
    patience=20,
    save=True
)
```

### Performance

| Metric | Value |
|--------|-------|
| **mAP@50** | 0.87 |
| **Inference Time (CPU)** | < 1 second |
| **Food Classes** | 80+ |
| **Model Size** | ~6MB |

---

## 🔌 API Endpoints

| Endpoint | Method | Description | Auth |
|----------|--------|-------------|------|
| `/api/analyze/` | POST | Upload image, return segmentation + calories | Required |
| `/api/foods/` | GET | List all supported food classes | Public |
| `/api/consultations/` | GET/POST | Manage consultations | Required |
| `/api/diet-plans/` | GET/POST | Manage diet plans | Required |
| `/api/auth/register/` | POST | Create new user account | Public |
| `/api/auth/login/` | POST | Authenticate user | Public |
| `/api/payments/` | POST | Process payment | Required |

---

## ⚡ Performance

| Scenario | Time |
|----------|------|
| Image upload + preprocessing | ~100ms |
| YOLOv8-seg inference (CPU) | ~300-500ms |
| Post-processing + calorie lookup | ~50ms |
| **Total response time** | **< 1 second** |

---

## 🔮 Future Improvements

- [ ] **Mobile App** — Flutter companion app
- [ ] **Multi-language** — French, Arabic support
- [ ] **Advanced Analytics** — Patient progress tracking
- [ ] **Cloud Migration** — AWS/GCP for scalability
- [ ] **GPU Acceleration** — CUDA support

---

## 📄 License

This project is licensed under the MIT License.

---

## 📬 Contact

**Serine Benmissi**

- 📧 [benmissi.dev@gmail.com](mailto:benmissi.dev@gmail.com)
- 💼 [linkedin.com/in/ben-missi-993269419](https://linkedin.com/in/ben-missi-993269419)
- 🌐 [portfolio-inky-three-33.vercel.app](https://portfolio-inky-three-33.vercel.app)

**⭐ Star this repo if you find it useful!**
