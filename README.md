🍎 AI Nutritionist
Full-Stack AI Platform for Intelligent Food Photo Analysis
https://python.org
https://www.djangoproject.com/
https://ultralytics.com/
https://render.com/
LICENSE
Live Demo: ai-nutritionist-lsha.onrender.com
📋 Table of Contents
Overview
Features
Tech Stack
Architecture
Installation
Usage
Model Training
API Endpoints
Screenshots
Performance
Future Improvements
Contributing
License
Contact
🎯 Overview
AI Nutritionist is a production-ready, full-stack web application that uses computer vision to analyze food photographs, automatically segment individual food items, and estimate their caloric content in real time.
Built from scratch as an end-to-end system, it demonstrates the ability to bridge deep learning, backend engineering, frontend development, and cloud deployment into a single cohesive product.
Why This Project?
Existing calorie-tracking apps rely on manual input or barcode scanning. AI Nutritionist eliminates friction by letting users simply take a photo — the system identifies food items, segments them individually, and returns nutritional data automatically.
✨ Features
Core Functionality
📸 Photo Upload — Drag-and-drop or click-to-upload food images
🎯 Instance Segmentation — YOLOv8-seg identifies and outlines each food item individually
📊 Calorie Estimation — Automatic calorie calculation per detected food item
📱 Responsive Design — Works seamlessly on desktop, tablet, and mobile
⚡ Real-Time Processing — Sub-second inference on optimized CPU deployment
Technical Features
🔄 RESTful API — Clean, documented endpoints for all operations
🔐 User Authentication — Secure session-based login and registration
📦 Database Persistence — SQLite3 with optimized schema for food items, users, and meal history
🚀 CI/CD Pipeline — Automated testing and deployment via GitHub Actions
☁️ Cloud Deployed — Live on Render with environment configuration
🛠 Tech Stack
Feuilles de calcul
Layer	Technology
Computer Vision	YOLOv8-seg (Ultralytics), PyTorch
Backend	Django 4.0+, Django REST Framework
Database	SQLite3 (production-ready schema)
Frontend	HTML5, CSS3, Vanilla JavaScript
Deployment	Render (Web Service + Static Files)
CI/CD	GitHub Actions
AI Tools	Cursor, GitHub Copilot (accelerated development)
Version Control	Git, GitHub
🏗 Architecture
plain
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Client        │────▶│   Django REST   │────▶│   YOLOv8-seg    │
│   (Browser)     │◀────│   API           │◀────│   Model         │
│                 │     │                 │     │                 │
│ • Upload Photo  │     │ • Image Upload  │     │ • Instance      │
│ • View Results  │     │ • Inference     │     │   Segmentation  │
│ • Meal History  │     │ • Calorie Calc  │     │ • Classify      │
└─────────────────┘     └─────────────────┘     └─────────────────┘
         │                       │                       │
         │              ┌────────┴────────┐               │
         │              │   SQLite3 DB    │               │
         │              │                 │               │
         │              │ • Users         │               │
         │              │ • Food Items    │               │
         └──────────────│ • Meal History  │───────────────┘
                        └─────────────────┘
Data Flow
User uploads food photo via drag-and-drop or file input
Image preprocessing — resize, normalize, format for model input
YOLOv8-seg inference — detects food items, generates segmentation masks
Post-processing — filter low-confidence detections, aggregate results
Calorie estimation — map detected classes to nutritional database
Response — return bounding boxes, segmentation masks, calorie data
Persistence — store results in database for meal history tracking
🚀 Installation
Prerequisites
Python 3.9+
pip
Git
Clone Repository
bash
git clone https://github.com/serinenadabenmissi-design/AI_nutritionist.git
cd AI_nutritionist
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
Download Model Weights
bash
# YOLOv8-seg model weights will download automatically on first run
# Or manually place your trained weights in:
# models/best.pt
Database Setup
bash
python manage.py migrate
python manage.py createsuperuser  # Optional: create admin account
Run Development Server
bash
python manage.py runserver
Visit http://127.0.0.1:8000 in your browser.
💻 Usage
Web Interface
Open the application in your browser
Click or drag a food photo onto the upload area
Wait for processing (typically under 1 second)
View results: detected food items with bounding boxes, segmentation masks, and calorie estimates
Register/login to save meal history
API Usage
bash
# Upload image for analysis
curl -X POST -F "image=@food_photo.jpg"   https://ai-nutritionist-lsha.onrender.com/api/analyze/

# Response format:
# {
#   "success": true,
#   "items": [
#     {"class": "apple", "confidence": 0.94, "calories": 95, "mask": "..."},
#     {"class": "banana", "confidence": 0.89, "calories": 105, "mask": "..."}
#   ],
#   "total_calories": 200,
#   "processing_time": "0.4s"
# }
🧠 Model Training
Dataset
80+ food categories covering fruits, vegetables, grains, proteins, and prepared foods
Custom annotated dataset with instance segmentation masks
Data augmentation: rotation, scaling, flipping, color jittering
Training Configuration
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
    device='cpu',  # or 'cuda' for GPU
    patience=20,
    save=True,
    project='runs/food_segmentation',
    name='exp01'
)
Performance Metrics
Feuilles de calcul
Metric	Value
mAP@50	0.87
mAP@50-95	0.72
Inference Time (CPU)	< 1 second
Classes	80+
Model Size	~6MB (YOLOv8n-seg)
🔌 API Endpoints
Feuilles de calcul
Endpoint	Method	Description
/api/analyze/	POST	Upload image, return segmentation + calories
/api/foods/	GET	List all supported food classes
/api/history/	GET	User's meal history (authenticated)
/api/history/	POST	Save meal to history (authenticated)
/api/auth/register/	POST	Create new user account
/api/auth/login/	POST	Authenticate and receive session
/api/auth/logout/	POST	End user session
📸 Screenshots
Upload Interface
Analysis Results
Meal History
⚡ Performance
Feuilles de calcul
Scenario	Time
Image upload + preprocessing	~100ms
YOLOv8-seg inference (CPU)	~300-500ms
Post-processing + calorie lookup	~50ms
Total response time	< 1 second
Optimization Techniques
Model quantization (INT8)
Input image resizing to 640x640
Batch inference for multiple images
Cached food-to-calorie mappings
Static file serving via CDN
🔮 Future Improvements
[ ] Mobile App — Flutter/React Native companion app
[ ] Multi-language Support — French, Arabic, Spanish
[ ] Nutritional Database Expansion — Macro and micronutrient tracking
[ ] User Profiles — Dietary preferences, allergies, goals
[ ] Meal Planning — Weekly meal suggestions based on history
[ ] Cloud Migration — AWS/GCP for scalability
[ ] GPU Acceleration — CUDA support for faster inference
[ ] Model Retraining Pipeline — Automated fine-tuning on new data
🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
Fork the repository
Create your feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request
📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
📬 Contact
Serine Benmissi
📧 Email: benmissi.dev@gmail.com
💼 LinkedIn: linkedin.com/in/ben-missi-993269419
🌐 Portfolio: portfolio-inky-three-33.vercel.app
🐱 GitHub: github.com/serinenadabenmissi-design
Live Demo: ai-nutritionist-lsha.onrender.com
"I don't just write code. I build systems that see, think, and decide — and ship them live."
⭐ Star this repo if you find it useful!
