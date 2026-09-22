# 🍎 AI Nutritionist

> Full-Stack AI Platform for Intelligent Food Photo Analysis & Nutrition Management

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?logo=python&logoColor=white)](https://python.org)
[![Django](https://img.shields.io/badge/Django-4.0+-092E20?logo=django&logoColor=white)](https://www.djangoproject.com/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-seg-111F4D?logo=ultralytics&logoColor=white)](https://ultralytics.com/)
[![Render](https://img.shields.io/badge/Deployed%20on-Render-46E3B7?logo=render&logoColor=white)](https://render.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**🚀 Live Demo:** [ai-nutritionist-lsha.onrender.com](https://ai-nutritionist-lsha.onrender.com)

<!-- Note if this was solo or team work, e.g.:
> Solo-built final-year project (PFE), from CV model training to deployment.
-->

---

## 📋 Table of Contents
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Screenshots](#-screenshots)
- [Installation](#-installation)
- [Usage](#-usage)
- [AI Model](#-ai-model)
- [API Endpoints](#-api-endpoints)
- [Performance](#-performance)
- [Future Improvements](#-future-improvements)
- [Contact](#-contact)

---

## ✨ Features

### 🔥 Core AI Features
- 📸 **AI Food Photo Analysis** — Upload a food photo, YOLOv8-seg identifies and segments each item
- 🎯 **Instance Segmentation** — Individual bounding boxes and masks per food item
- 📊 **Calorie Estimation** — Automatic nutritional calculation per detected item
- ⚡ **Real-Time Processing** — Sub-second inference on optimized CPU deployment

### 🏥 Platform Features
- 👤 **Multi-Role System** — Patients, Nutritionists, and Admins
- 📅 **Consultation Booking** — Patients book appointments with nutritionists
- 📋 **Diet Plan Management** — Nutritionists create personalized diet plans
- 💳 **Payment Integration** — Secure payments via <!-- name your provider, e.g. Stripe/PayPal/CIB -->
- 📱 **Responsive Design** — Desktop, tablet, and mobile

### 🛠 Technical Features
- 🔄 **RESTful API** — Django REST Framework endpoints
- 🔐 **Authentication** — Registration, login, role-based access control
- 📦 **Database** — SQLite3, schema for users, consultations, diet plans, meal history
- 🚀 **CI/CD** — Automated deployment via GitHub Actions
- ☁️ **Cloud Deployed** — Live on Render with environment-based configuration

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Computer Vision** | YOLOv8-seg (Ultralytics), PyTorch |
| **Backend** | Django 4.0+, Django REST Framework |
| **Database** | SQLite3 |
| **Frontend** | HTML5, CSS3, JavaScript |
| **Payment** | <!-- name your gateway --> |
| **Deployment** | Render (Web Service) |
| **CI/CD** | GitHub Actions |
| **Version Control** | Git, GitHub |

---

## 🏗 Architecture

```
┌──────────────────┐      ┌───────────────────┐      ┌──────────────────┐
│      Client       │ ───► │    Django REST     │ ───► │    YOLOv8-seg     │
│    (Browser)       │ ◄─── │        API          │ ◄─── │       Model        │
│                    │      │                    │      │                    │
│ • Upload photo     │      │ • Image upload     │      │ • Instance         │
│ • Book consult      │      │ • Inference        │      │   segmentation      │
│ • View diet plan    │      │ • Calorie calc     │      │ • Classification    │
│ • Payment           │      │ • Auth / roles     │      │                    │
└──────────────────┘      └─────────┬──────────┘      └──────────────────┘
                                      │
                                      ▼
                          ┌────────────────────┐
                          │     SQLite3 DB      │
                          │                     │
                          │ • Users             │
                          │   (patient/nutri-   │
                          │    tionist/admin)   │
                          │ • Consultations     │
                          │ • Diet plans        │
                          │ • Meal history       │
                          │ • Payments          │
                          └────────────────────┘
```

---

## 📸 Screenshots

### 🏠 Home
![Home](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/home.png)

### 🔐 Login
![Login](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/login.png)

### 👤 User Dashboard
![User Dashboard](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/userdash.png)

### 🤖 AI Food Segmentation
![AI Segmentation](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/AI%20seg.png)

### 🥗 Nutritionist Dashboard — Consultations
![Nutridash Consultations](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/nutridash%20cons.png)

### 📋 Nutritionist Dashboard — Diet Plans
![Nutridash Dietplan](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/nutridash%20dietplan.png)

### 📅 Book a Consultation
![User Book Consultation](https://raw.githubusercontent.com/ramdaninourhane26-hash/pfe/main/screenshots/user%20book%20cons.png)

---

## 🚀 Installation

### Prerequisites
- Python 3.9+, pip, Git

### Setup

```bash
git clone https://github.com/ramdaninourhane26-hash/pfe.git
cd pfe

python -m venv venv
# Windows: venv\Scripts\activate
# macOS/Linux: source venv/bin/activate

pip install -r requirements.txt

# Copy env template and fill in your own secrets (SECRET_KEY, payment keys, etc.)
cp .env.example .env

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Visit `http://127.0.0.1:8000`

---

## 💻 Usage

**Patients:** register → upload food photos for AI analysis → book consultations → view diet plans → pay securely.

**Nutritionists:** register → manage consultation requests → create personalized diet plans → track patient progress.

**Admins:** access dashboard → manage users and roles → monitor platform activity.

---

## 🧠 AI Model

Trained a YOLOv8-seg model on a food image dataset <!-- specify: public dataset fine-tuned, or fully custom-labeled --> to segment and classify food items directly from photos.

```python
from ultralytics import YOLO

model = YOLO('yolov8n-seg.pt')
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

| Metric | Value |
|--------|-------|
| **mAP@50** | 0.87 |
| **Inference Time (CPU)** | < 1 second |
| **Food Classes** | 80+ |
| **Model Size** | ~6 MB |

---

## 🔌 API Endpoints

| Endpoint | Method | Description | Auth |
|----------|--------|-------------|------|
| `/api/analyze/` | POST | Upload image, return segmentation + calories | Required |
| `/api/foods/` | GET | List supported food classes | Public |
| `/api/consultations/` | GET/POST | Manage consultations | Required |
| `/api/diet-plans/` | GET/POST | Manage diet plans | Required |
| `/api/auth/register/` | POST | Create account | Public |
| `/api/auth/login/` | POST | Authenticate | Public |
| `/api/payments/` | POST | Process payment | Required |

---

## ⚡ Performance

| Scenario | Time |
|----------|------|
| Image upload + preprocessing | ~100ms |
| YOLOv8-seg inference (CPU) | ~300–500ms |
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

MIT License — see [LICENSE](LICENSE).

---

## 📬 Contact

**Serine Benmissi**

- 📧 [benmissi.dev@gmail.com](mailto:benmissi.dev@gmail.com)
- 💼 [linkedin.com/in/ben-missi-993269419](https://linkedin.com/in/ben-missi-993269419)
- 🌐 [portfolio-inky-three-33.vercel.app](https://portfolio-inky-three-33.vercel.app)

**⭐ Star this repo if you find it useful!**
