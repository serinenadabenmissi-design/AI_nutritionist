🍎 AI Nutritionist
Full-Stack AI Platform for Intelligent Food Photo Analysis & Nutrition Management
https://python.org
https://www.djangoproject.com/
https://ultralytics.com/
https://render.com/
LICENSE
🚀 Live Demo: ai-nutritionist-lsha.onrender.com
📸 Screenshots
🏠 Home Page
 Home 
🔐 Login Page
 Login 
👤 User Dashboard
 User Dashboard 
🤖 AI Food Segmentation
 AI Segmentation 
🥗 Nutritionist Dashboard - Consultations
 Nutridash Consultations 
📋 Nutritionist Dashboard - Diet Plans
 Nutridash Dietplan 
📅 User Book Consultation
 User Book Consultation 
✨ Features
🔥 Core AI Features
📸 AI Food Photo Analysis — Upload a food photo, YOLOv8-seg identifies and segments each food item
🎯 Instance Segmentation — Individual bounding boxes and masks for each food item
📊 Calorie Estimation — Automatic nutritional calculation per detected item
⚡ Real-Time Processing — Sub-second inference on optimized CPU deployment
🏥 Platform Features
👤 Multi-Role System — Patients, Nutritionists, and Admins
📅 Consultation Booking — Patients book appointments with nutritionists
📋 Diet Plan Management — Nutritionists create personalized diet plans
💳 Payment Integration — Secure payment processing for consultations
📱 Responsive Design — Works on desktop, tablet, and mobile
🛠 Technical Features
🔄 RESTful API — Clean, documented Django REST Framework endpoints
🔐 Authentication — Secure user registration, login, and role-based access
📦 Database — SQLite3 with optimized schema for users, consultations, diet plans, and meal history
🚀 CI/CD Pipeline — Automated deployment via GitHub Actions
☁️ Cloud Deployed — Live on Render with environment configuration
🛠 Tech Stack
Feuilles de calcul
Layer	Technology
Computer Vision	YOLOv8-seg (Ultralytics), PyTorch
Backend	Django 4.0+, Django REST Framework
Database	SQLite3
Frontend	HTML5, CSS3, JavaScript
Payment	Integrated payment gateway
Deployment	Render (Web Service)
CI/CD	GitHub Actions
AI Tools	Cursor, GitHub Copilot
Version Control	Git, GitHub
🏗 Architecture
plain
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
🚀 Installation
Prerequisites
Python 3.9+
pip
Git
Clone Repository
bash
git clone https://github.com/ramdaninourhane26-hash/pfe.git
cd pfe
Create Virtual Environment
bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
Install Dependencies
bash
pip install -r requirements.txt
Database Setup
bash
python manage.py migrate
python manage.py createsuperuser
Run Development Server
bash
python manage.py runserver
Visit http://127.0.0.1:8000
💻 Usage
For Patients
Register as a patient
Upload food photos for AI analysis
Book consultations with nutritionists
View personalized diet plans
Make payments securely
For Nutritionists
Register as a nutritionist
Manage consultation requests
Create personalized diet plans
Track patient progress
For Admins
Access admin dashboard
Manage users and roles
Monitor platform activity
🧠 AI Model
YOLOv8-seg Configuration
Python
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
Performance
Feuilles de calcul
Metric	Value
mAP@50	0.87
Inference Time (CPU)	< 1 second
Food Classes	80+
Model Size	~6MB
🔌 API Endpoints
Feuilles de calcul
Endpoint	Method	Description	Auth
/api/analyze/	POST	Upload image, return segmentation + calories	Required
/api/foods/	GET	List all supported food classes	Public
/api/consultations/	GET/POST	Manage consultations	Required
/api/diet-plans/	GET/POST	Manage diet plans	Required
/api/auth/register/	POST	Create new user account	Public
/api/auth/login/	POST	Authenticate user	Public
/api/payments/	POST	Process payment	Required
⚡ Performance
Feuilles de calcul
Scenario	Time
Image upload + preprocessing	~100ms
YOLOv8-seg inference (CPU)	~300-500ms
Post-processing + calorie lookup	~50ms
Total response time	< 1 second
🔮 Future Improvements
[ ] Mobile App — Flutter companion app
[ ] Multi-language — French, Arabic support
[ ] Advanced Analytics — Patient progress tracking
[ ] Cloud Migration — AWS/GCP for scalability
[ ] GPU Acceleration — CUDA support
📄 License
This project is licensed under the MIT License.
📬 Contact
Serine Benmissi
📧 benmissi.dev@gmail.com
💼 linkedin.com/in/ben-missi-993269419
🌐 portfolio-inky-three-33.vercel.app
⭐ Star this repo if you find it useful!
