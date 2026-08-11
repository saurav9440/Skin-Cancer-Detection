# Skin Cancer Detection and Classification Using Deep Learning

A hybrid deep learning-based computer-aided diagnostic system for detecting and classifying skin diseases from dermoscopic images.

The proposed system combines **U-Net lesion segmentation**, **EfficientNetV2-S feature extraction**, and a **Vision Transformer (ViT)** to analyze both local and global characteristics of skin lesions.

## Project Overview

The system follows a two-stage hybrid deep learning pipeline:

1. **Lesion Segmentation** using U-Net
2. **Feature Extraction and Classification** using EfficientNetV2-S + Vision Transformer (ViT)

A segmentation-guided **4-channel input** is created by combining the normalized RGB image with the lesion mask. The final framework performs **12-class skin disease classification** and reports a **validation accuracy of 89.14%**.

## Objectives

- Automate skin disease detection from dermoscopic images.
- Segment lesions using U-Net.
- Extract local features using EfficientNetV2-S.
- Capture global lesion structure using Vision Transformer.
- Handle class imbalance using balanced sampling.
- Improve prediction stability using Test-Time Augmentation (TTA).
- Provide prediction labels, confidence scores, segmentation masks and visualization.
- Develop a practical computer-aided diagnostic prototype.

## Proposed Architecture

```text
Dermoscopic Image
       |
       v
Image Preprocessing
       |
       v
U-Net Lesion Segmentation
       |
       v
Lesion Mask + Normalized RGB
       |
       v
4-Channel Input
       |
       v
EfficientNetV2-S
(Local Features)
       |
       v
Vision Transformer
(Global Features)
       |
       v
Pooling + Dropout
       |
       v
Softmax Classifier
       |
       v
12-Class Disease Prediction
```

## Methodology

### Image Preprocessing

- Image resizing
- RGB conversion
- Normalization
- Noise reduction
- Hair and artifact removal
- Data augmentation

### Lesion Segmentation

U-Net identifies the lesion region and produces a binary lesion mask. This helps reduce irrelevant background information such as healthy skin, hair, shadows and other artifacts.

### Segmentation-Guided 4-Channel Input

```text
RGB Image   -> 3 Channels
Lesion Mask -> 1 Channel
                    |
                    v
             4-Channel Tensor
```

### EfficientNetV2-S

EfficientNetV2-S extracts detailed local features such as texture, color variation, lesion boundaries and fine-grained skin patterns.

### Vision Transformer

ViT captures global information including lesion structure, shape, symmetry, spatial relationships and long-range dependencies.

### Classification

The final representation is processed through global average pooling, dropout and a fully connected softmax classification layer to predict one of 12 disease categories.

### Balanced Sampling

Balanced sampling is used to reduce bias caused by class imbalance and improve minority-class learning.

### Test-Time Augmentation

Multiple transformed versions of an input image are evaluated and their predictions are combined to obtain a more stable final prediction.

## Dataset

The project uses the **HAM10000 (Human Against the Machine with 10000 training images)** dermoscopic image dataset.

The dataset contains dermoscopic images, disease metadata and multiple skin disease categories with class imbalance.

> The complete dataset is not included in this repository.

## Results

| Metric | Result |
|---|---|
| Classification Type | Multi-Class |
| Number of Classes | 12 |
| Validation Accuracy | **89.14%** |
| Segmentation Model | U-Net |
| Feature Extractor | EfficientNetV2-S |
| Global Feature Model | Vision Transformer |
| Input | 4-Channel RGB + Mask |
| Class Balancing | Balanced Sampling |
| Prediction Enhancement | TTA |

## Web Application

The project includes a web-based interface.

### Frontend
- EJS
- HTML5
- CSS3
- JavaScript
- jsPDF

### Backend
- Node.js
- Express.js

### Database
- MongoDB
- Mongoose

### Features
- User authentication
- Image upload
- Prediction visualization
- Scan history
- Dashboard
- Diagnostic report generation

## Project Structure

```text
Skin-Cancer-Detection/
|
├── frontend/
│   ├── views/
│   ├── public/
│   └── routes/
|
├── backend/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── server.js
|
├── ml/
│   ├── preprocessing/
│   ├── segmentation/
│   ├── classification/
│   ├── evaluation/
│   └── inference/
|
├── models/
│   ├── unet_model.keras
│   └── classifier_model.keras
|
├── screenshots/
├── requirements.txt
├── package.json
└── README.md
```

> Adjust the structure above to match the actual repository structure.

## Technologies Used

- Python
- TensorFlow
- Keras
- OpenCV
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- U-Net
- EfficientNetV2-S
- Vision Transformer
- Node.js
- Express.js
- EJS
- MongoDB
- Mongoose
- JavaScript
- HTML5
- CSS3

## Installation

### Clone Repository

```bash
git clone https://github.com/YOUR-USERNAME/Skin-Cancer-Detection.git
cd Skin-Cancer-Detection
```

### Python Environment

```bash
python -m venv venv
```

Windows:

```bash
venv\\Scripts\\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

### Install Python Dependencies

```bash
pip install -r requirements.txt
```

### Install Node Dependencies

```bash
npm install
```

## Environment Variables

Create a `.env` file:

```env
MONGO_URI=your_mongodb_connection_string
PORT=5000
```

Do not upload `.env` to GitHub.

Recommended `.gitignore` entries:

```text
.env
venv/
__pycache__/
node_modules/
*.h5
*.keras
```

## Running the Application

Start the Node.js backend:

```bash
node server.js
```

If the ML component has a Python entry point:

```bash
python app.py
```

## Evaluation

The classification system uses:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Segmentation can be evaluated using IoU/Dice coefficient where applicable.

## System Workflow

```text
User
 |
 v
Upload Dermoscopic Image
 |
 v
Preprocessing
 |
 v
U-Net Segmentation
 |
 v
Lesion Mask
 |
 v
RGB + Mask
 |
 v
4-Channel Input
 |
 v
EfficientNetV2-S
 |
 v
Local Features
 |
 v
Vision Transformer
 |
 v
Global Features
 |
 v
Classification
 |
 v
Disease + Confidence
 |
 +--> Segmentation Visualization
 +--> Prediction Result
 +--> Scan History
 +--> Diagnostic Report
```

## Team

| Name | Role |
|---|---|
| **Revan Kale** | Research, Dataset Analysis & Documentation |
| **Saurav Mane** | U-Net Segmentation |
| **Omkar Padule** | EfficientNetV2-S & Vision Transformer |
| **Onkar Pandhare** | Testing, Evaluation & System Integration |

### Project Guide

**Mrs. Y. N. Sakhare**

Department of Information Technology  
Vidya Pratishthan's Kamalnayan Bajaj Institute of Engineering and Technology, Baramati

## Academic Project

**Project Stage-II — 2025–2026**

Department of Information Technology  
Vidya Pratishthan's Kamalnayan Bajaj Institute of Engineering and Technology, Baramati, Maharashtra, India

Submitted under **Savitribai Phule Pune University, Pune**.

## Disclaimer

This project is developed for **academic and research purposes**.

The system is intended as a computer-aided diagnostic support tool and should not be considered a replacement for professional medical diagnosis. Final diagnosis and treatment decisions must be made by qualified healthcare professionals.

## Future Scope

- Clinical validation using real-world clinical datasets
- Larger and more diverse datasets
- Improved segmentation accuracy
- Additional disease categories
- Improved model explainability
- Integration of clinical metadata
- Mobile application deployment
- Real-time healthcare system integration
- Improved computational efficiency
- Continuous model optimization

## References

1. L. Riaz et al., **"A Comprehensive Joint Learning System to Detect Skin Cancer,"** IEEE Access, 2023.
2. R. Raja Sekar et al., **"Skin Cancer Prediction Using Deep Learning Techniques,"** ICSPC, 2023.
3. J. R. Hagerty et al., **"Deep Learning and Handcrafted Method Fusion: Higher Diagnostic Accuracy for Melanoma Dermoscopy Images,"** IEEE Journal of Biomedical and Health Informatics, 2019.
4. S. Archana and N. Shyamsundar, **"Computational Intelligence for Detection of Skin Cancer Using Deep Learning Classifiers,"** 2021.
5. P. Thapar et al., **"A Novel Hybrid Deep Learning Approach for Skin Lesion Segmentation and Classification,"** Journal of Healthcare Engineering, 2022.

## Key Highlights

- Hybrid Deep Learning Architecture
- U-Net Lesion Segmentation
- EfficientNetV2-S Feature Extraction
- Vision Transformer for Global Feature Learning
- Segmentation-Guided 4-Channel Input
- Balanced Class Sampling
- Test-Time Augmentation
- 12-Class Skin Disease Classification
- 89.14% Reported Validation Accuracy
- Full-Stack Web Interface
- MongoDB-Based Scan History
- Diagnostic Report Generation
