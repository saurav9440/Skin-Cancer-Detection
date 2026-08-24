# 🩺 DermaScan – AI-Powered Skin Disease Detection System

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-Express.js-green?style=for-the-badge&logo=node.js">
  <img src="https://img.shields.io/badge/Python-Flask-blue?style=for-the-badge&logo=flask">
  <img src="https://img.shields.io/badge/TensorFlow-Deep%20Learning-orange?style=for-the-badge&logo=tensorflow">
  <img src="https://img.shields.io/badge/MongoDB-Database-green?style=for-the-badge&logo=mongodb">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge">
</p>

---

# 📌 Overview

DermaScan is a **Full-Stack AI-Powered Skin Disease Detection System** that detects skin cancer and multiple skin diseases from uploaded images using Deep Learning.

The application combines a modern web interface with a hybrid AI architecture consisting of **U-Net**, **EfficientNetV2-S**, and **Vision Transformer (ViT)** to provide accurate disease predictions with approximately **89.14% validation accuracy**.

Users can securely upload skin images, receive AI-generated predictions with confidence scores, visualize the complete image processing pipeline, download PDF reports, and maintain a personalized scan history.

---

# ✨ Features

* 🩺 AI-powered skin disease detection
* 🧠 Hybrid Deep Learning Architecture
* 🔍 U-Net based lesion segmentation
* ⚡ EfficientNetV2-S feature extraction
* 🤖 Vision Transformer (ViT) classification
* 🔄 Test-Time Augmentation (TTA)
* 🎯 Automatic ROI extraction
* 📊 Confidence score prediction
* 🖼️ Image preprocessing visualization
* 📄 PDF report generation
* 👤 Secure user authentication
* 🔐 Password hashing using bcrypt
* 📂 Scan history management
* 📱 Fully responsive dashboard
* 💾 MongoDB database integration

---

# 🏗️ System Architecture

```text
                User
                  │
                  ▼
         EJS Frontend (UI)
                  │
                  ▼
         Node.js + Express
                  │
       REST API Communication
                  │
                  ▼
            Flask ML API
                  │
                  ▼
             Image Upload
                  │
                  ▼
              U-Net Model
       (Lesion Segmentation)
                  │
                  ▼
      Image Preprocessing &
      ROI Mask Generation
                  │
                  ▼
        EfficientNetV2-S
     (Feature Extraction)
                  │
                  ▼
      Vision Transformer
          (Classification)
                  │
                  ▼
        Disease Prediction
                  │
                  ▼
      MongoDB (Prediction History)
```

---

# 🧠 AI Model Pipeline

## Step 1 — Image Upload

The user uploads a dermoscopic or skin lesion image through the web application.

↓

## Step 2 — U-Net Segmentation

The uploaded image is processed using a **U-Net segmentation model** to generate an accurate lesion mask.

This helps:

* Remove background noise
* Focus on affected skin regions
* Improve classification accuracy

↓

## Step 3 — Image Preprocessing

The segmented image undergoes:

* Image resizing (256 × 256)
* RGB normalization
* Otsu Thresholding
* ROI extraction
* Automatic mask generation

↓

## Step 4 — EfficientNetV2-S

EfficientNetV2-S extracts deep visual features from the segmented lesion.

It provides:

* High accuracy
* Fast inference
* Optimized feature extraction
* Better generalization

↓

## Step 5 — Vision Transformer (ViT)

The extracted features are passed to a Vision Transformer.

ViT uses **Self-Attention** to understand relationships between different regions of the image and improve classification performance.

↓

## Step 6 — Test-Time Augmentation (TTA)

During prediction, multiple augmented versions of the same image are generated.

Examples include:

* Horizontal Flip
* Rotation
* Probability Averaging

This significantly improves prediction robustness.

↓

## Step 7 — Disease Classification

The model predicts one of the supported disease classes and returns:

* Disease Name
* Cancer / Non-Cancer
* Confidence Score
* Processing Stage Images

---

# 📊 Supported Diseases

* Melanoma (mel)
* Basal Cell Carcinoma (bcc)
* Actinic Keratosis (akiec)
* Benign Keratosis (bkl)
* Dermatofibroma (df)
* Melanocytic Nevi (nv)
* Vascular Lesion (vasc)
* Burn
* Cut
* Abrasion
* Bruise

---

# 📸 Screenshots

## 🏠 Home Page

![DermaScan Home Page](images/home%20page.png)

---

## 🔐 Login Page

![DermaScan Login Page](images/login.png)

---

## 🧪 Test Case

![DermaScan Test Case](images/TestCase1.jpeg)

---

## 📊 Scan History

![DermaScan History Page](images/history.png)

---

# 💻 Tech Stack

## Frontend

* EJS
* HTML5
* CSS3
* JavaScript

## Backend

* Node.js
* Express.js

## Machine Learning

* Python
* Flask
* TensorFlow
* U-Net
* EfficientNetV2-S
* Vision Transformer (ViT)
* OpenCV
* NumPy

## Database

* MongoDB
* Mongoose

## Authentication

* Express Session
* bcrypt

## Libraries

* Multer
* jsPDF
* Axios

---

# 📂 Project Structure

```text
DermaScan
│
├── models/
├── routes/
├── public/
│   ├── css/
│   ├── js/
│   └── images/
│
├── uploads/
│
├── images/
│   ├── home page.png
│   ├── login.png
│   ├── TestCase1.jpeg
│   └── history.png
│
├── views/
│   ├── partials/
│   ├── login.ejs
│   ├── signup.ejs
│   ├── result.ejs
│   ├── history.ejs
│   └── index.ejs
│
├── ml-api/
│   ├── app.py
│   ├── best_skin_disease_model.keras
│   └── static/
│
├── app.js
├── package.json
└── README.md
```

---

# 🔄 Workflow

1. User uploads a skin image.
2. Express receives the uploaded image.
3. Multer stores the image temporarily.
4. Image is sent to Flask API.
5. U-Net segments the lesion.
6. Image preprocessing generates ROI and mask.
7. EfficientNetV2-S extracts deep features.
8. Vision Transformer performs classification.
9. Test-Time Augmentation improves prediction reliability.
10. Prediction result is returned.
11. Result is stored in MongoDB.
12. User can view previous scans and download reports.

---

# 📈 Model Performance

| Metric              | Value                                         |
| ------------------- | --------------------------------------------- |
| Validation Accuracy | **89.14%**                                    |
| Architecture        | U-Net + EfficientNetV2-S + Vision Transformer |
| Input Size          | 256 × 256 × 4                                 |
| Classification      | Multi-Class                                   |
| Prediction          | Cancer / Non-Cancer                           |

---

# 🚀 Installation

## Clone Repository

```bash
git clone https://github.com/onkar-pandhare/DermaScan.git
```

## Install Backend Dependencies

```bash
npm install
```

## Install Python Dependencies

```bash
pip install -r requirements.txt
```

## Start Flask API

```bash
python app.py
```

## Start Express Server

```bash
npm start
```

Open:

```text
http://localhost:5000
```

---

# 🔮 Future Enhancements

* Google OAuth Authentication
* Cloud Deployment
* Email Report Sharing
* Doctor Recommendation System
* Appointment Booking
* Mobile Application
* Real-time Camera Detection
* Medical Report Analytics

---

# 👨‍💻 Developer

**Onkar Pandhare**

Information Technology Engineer

📧 Email: [onkarpandhare22@gmail.com](mailto:onkarpandhare22@gmail.com)

🔗 GitHub: https://github.com/onkar-pandhare

🔗 LinkedIn: [www.linkedin.com/in/onkar-pandhare](http://www.linkedin.com/in/onkar-pandhare)

---

# ⭐ Support

If you found this project useful, please consider giving it a ⭐ on GitHub.

It motivates me to build more impactful open-source projects.

---

## 📜 License

This project is developed for educational and research purposes.
