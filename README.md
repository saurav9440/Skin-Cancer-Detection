🩺 Skin Disease Detection and Classification Using Deep Learning

<p align="center">
  <img src="https://img.shields.io/badge/Python-Deep%20Learning-blue?style=for-the-badge&logo=python">
  <img src="https://img.shields.io/badge/TensorFlow-Keras-orange?style=for-the-badge&logo=tensorflow">
  <img src="https://img.shields.io/badge/U--Net-Segmentation-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Vision%20Transformer-ViT-purple?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge">
</p>

📌 Overview

This project presents a deep learning-based skin disease detection and classification system developed as a Final Year Project.

The proposed framework combines lesion segmentation using U-Net with a hybrid classification architecture using EfficientNetV2-S and Vision Transformer (ViT).

The segmentation stage identifies the lesion region using a mask, allowing the classification model to focus on the affected region rather than irrelevant background information.

The classification pipeline uses a 4-channel input consisting of RGB image information and the lesion mask. EfficientNetV2-S is used to learn detailed local visual features, while the Vision Transformer captures global relationships and structural information within the lesion.

The project also incorporates balanced sampling, data augmentation, focal loss and Test-Time Augmentation (TTA) to improve classification performance and robustness.

🎯 Objectives

Develop an automated skin disease detection and classification system.

Segment the lesion region using U-Net.

Generate and utilize lesion masks for classification.

Combine RGB information with the lesion mask as a 4-channel input.

Extract detailed visual features using EfficientNetV2-S.

Capture global spatial relationships using Vision Transformer (ViT).

Address class imbalance using balanced sampling.

Improve model robustness using Test-Time Augmentation (TTA).

Evaluate the final classifier using standard classification metrics.

🏗️ System Architecture

                 Dermoscopic Image
                         │
                         ▼
                Image Preprocessing
                         │
                         ▼
                 Lesion Segmentation
                         │
                         ▼
                      U-Net
                         │
                         ▼
                   Lesion Mask
                         │
             ┌───────────┴───────────┐
             │                       │
             ▼                       ▼
        RGB Image              Lesion Mask
             │                       │
             └───────────┬───────────┘
                         ▼
                 4-Channel Input
                  RGB + Mask
                         │
                         ▼
                 EfficientNetV2-S
                Local Feature Learning
                         │
                         ▼
                 Vision Transformer
                Global Feature Learning
                         │
                         ▼
              Pooling + Classification
                         │
                         ▼
                 Disease Prediction
                         │
                         ▼
             Class + Confidence Score

🧠 Methodology

Step 1 — Image Preprocessing

The input dermoscopic images are prepared before being passed to the deep learning models.

The preprocessing pipeline includes:

Image resizing

Pixel normalization

Image format handling

Data augmentation during training

Lesion-region preparation

Step 2 — Lesion Mask Generation

Initial lesion masks are generated using HSV/HSL-based image processing.

These masks provide an approximate representation of the lesion region and are used as the target information for training the segmentation model.

The generated masks help identify the region of interest while reducing irrelevant background information.

Step 3 — U-Net Segmentation

A U-Net architecture is trained using the generated lesion masks.

The U-Net follows an encoder-decoder architecture:

Input Image
     │
     ▼
Encoder
     │
     ├── Feature Extraction
     ├── Downsampling
     └── Context Learning
     │
     ▼
Bottleneck
     │
     ▼
Decoder
     │
     ├── Upsampling
     ├── Feature Reconstruction
     └── Skip Connections
     │
     ▼
Predicted Lesion Mask

The trained U-Net can then predict a lesion mask for a new input image.

Step 4 — 4-Channel Input

The predicted lesion mask is combined with the original RGB image.

RGB Image  → 3 channels
Mask       → 1 channel
                    │
                    ▼
             4-Channel Input

This gives the classification model both the original visual information and explicit lesion-region information.

Step 5 — EfficientNetV2-S

EfficientNetV2-S is used for feature extraction.

It learns detailed local characteristics such as:

Texture

Color patterns

Lesion boundaries

Fine-grained visual patterns

Local structural information

Step 6 — Vision Transformer (ViT)

The extracted feature representation is further processed using a Vision Transformer.

ViT uses self-attention to learn relationships between different regions of the feature representation.

It helps capture:

Global lesion structure

Shape

Symmetry

Spatial relationships

Long-range dependencies

Step 7 — Classification

The learned features are passed to the final classification stage.

The classification pipeline produces:

Predicted disease class

Class probability

Confidence score

Step 8 — Balanced Sampling

The dataset contains class imbalance.

A balanced generator is used during training to sample images from different classes more uniformly.

This helps prevent the model from becoming overly biased toward classes with a larger number of training samples.

Step 9 — Focal Loss

Categorical Focal Crossentropy is used as the classification loss.

Focal loss gives more emphasis to difficult training examples and helps address the effect of class imbalance.

The implementation uses:

Gamma = 2.0

Label smoothing = 0.1

Step 10 — Test-Time Augmentation

Test-Time Augmentation (TTA) is used during final prediction.

Multiple transformed versions of an input image can be evaluated and their predictions combined.

This helps improve prediction stability and robustness.

📊 Dataset

The project uses dermoscopic skin lesion images based on the HAM10000 dataset and the prepared project dataset.

The project dataset contains original images and corresponding lesion masks used for the segmentation and classification pipeline.

The dataset contains multiple skin disease categories and exhibits class imbalance, which is addressed during model training.

The complete image dataset is not included in this GitHub repository because of its large size.

📈 Model Performance

The project reports a validation accuracy of 89.14% for the classification system.

Component

Details

Segmentation

U-Net

Mask Generation

HSV/HSL-based preprocessing

Classification Backbone

EfficientNetV2-S

Global Feature Learning

Vision Transformer (ViT)

Input

RGB + Lesion Mask

Input Channels

4

Classification

Multi-Class

Validation Accuracy

89.14%

Class Balancing

Balanced Sampling

Loss Function

Categorical Focal Crossentropy

Prediction Enhancement

Test-Time Augmentation

The 89.14% value is reported as validation accuracy. Test accuracy should be reported separately if obtained from the final held-out test evaluation.

💻 Technologies Used

Programming

Python

Jupyter Notebook

Deep Learning

TensorFlow

Keras

U-Net

EfficientNetV2-S

Vision Transformer (ViT)

Computer Vision

OpenCV

HSV/HSL image processing

Image preprocessing

Image augmentation

Lesion segmentation

Machine Learning

Scikit-learn

Classification Report

Confusion Matrix

Accuracy

Precision

Recall

F1-score

Data Processing

NumPy

Pandas

📂 Repository Structure

DermaScan/
│
├── screenshots/
│
├── U-Net.ipynb
│
├── Main_Model.ipynb
│
└── README.md

U-Net Notebook

The U-Net notebook contains the lesion segmentation workflow, including:

Dataset preparation

Mask loading

Image preprocessing

U-Net architecture

Model training

Segmentation evaluation

Predicted mask generation

Main Model Notebook

The main notebook contains the classification workflow, including:

Dataset preparation

Balanced data generation

4-channel image + mask preparation

EfficientNetV2-S feature extraction

Vision Transformer integration

Model training

Validation

Test evaluation

TTA-based prediction

Classification metrics

🔄 Complete Workflow

Dataset
   │
   ▼
Original Dermoscopic Images
   │
   ▼
HSV/HSL-Based Mask Generation
   │
   ▼
Training Masks
   │
   ▼
U-Net Training
   │
   ▼
Predicted Lesion Masks
   │
   ▼
RGB Image + Predicted Mask
   │
   ▼
4-Channel Input
   │
   ▼
EfficientNetV2-S
   │
   ▼
Local Features
   │
   ▼
Vision Transformer
   │
   ▼
Global Features
   │
   ▼
Classification Layer
   │
   ▼
Skin Disease Prediction
   │
   ▼
Confidence + Evaluation Metrics

📸 Screenshots

Project screenshots are included in the screenshots/ directory.

Add your screenshots to the folder and update the filenames below to match the actual files in your repository.

screenshots/
├── login.png
├── dashboard.png
├── upload.png
├── segmentation.png
├── prediction.png
└── report.png

Example:

![Prediction Result](screenshots/prediction.png)

🧪 Evaluation

The classification model can be evaluated using:

Accuracy

Precision

Recall

F1-score

Confusion Matrix

Classification Report

The segmentation model can be evaluated using appropriate segmentation metrics such as:

IoU

Dice Coefficient

🚀 How to Use the Notebooks

1. U-Net Segmentation

Open:

U-Net.ipynb

Set the dataset paths according to your environment and execute the cells in sequence.

The notebook trains the U-Net model and generates predicted lesion masks.

2. Main Classification Model

Open:

Main_Model.ipynb

Set the image and mask paths and execute the cells in sequence.

The notebook performs classification using the segmentation-guided hybrid deep learning architecture.

Dataset paths may need to be changed depending on whether the notebooks are executed on Kaggle, Google Colab, or a local machine.

🎓 Academic Project

Final Year Project — Skin Disease Detection and Classification Using Deep Learning

Department of Information Technology

Vidya Pratishthan's Kamalnayan Bajaj Institute of Engineering and Technology, Baramati

Savitribai Phule Pune University, Pune

👥 Project Team

This project was developed as a group Final Year Project.

Add the final team-member names and individual contributions exactly as listed in your final project report.

Team Member

Contribution

Team Member 1

Project / Research

Team Member 2

U-Net Segmentation

Team Member 3

EfficientNetV2-S & ViT

Team Member 4

Testing & Integration

Replace the placeholders above with the exact names and contributions from your final report.

⚠️ Disclaimer

This project is developed for academic and research purposes.

The system is intended as a computer-aided diagnostic support system and should not be considered a replacement for professional medical diagnosis.

Final diagnosis and treatment decisions must be made by qualified healthcare professionals.

🔮 Future Scope

Improve lesion segmentation accuracy.

Train using larger and more diverse datasets.

Perform clinical validation using real-world clinical data.

Improve model explainability.

Integrate additional clinical metadata.

Support additional skin disease categories.

Optimize the model for mobile and edge-device deployment.

Develop a complete clinical decision-support application.

Improve inference speed and computational efficiency.

📚 References

L. Riaz et al., "A Comprehensive Joint Learning System to Detect Skin Cancer," IEEE Access, 2023.

R. Raja Sekar et al., "Skin Cancer Prediction Using Deep Learning Techniques," ICSPC, 2023.

J. R. Hagerty et al., "Deep Learning and Handcrafted Method Fusion: Higher Diagnostic Accuracy for Melanoma Dermoscopy Images," IEEE Journal of Biomedical and Health Informatics, 2019.

S. Archana and N. Shyamsundar, "Computational Intelligence for Detection of Skin Cancer Using Deep Learning Classifiers," 2021.

P. Thapar et al., "A Novel Hybrid Deep Learning Approach for Skin Lesion Segmentation and Classification," Journal of Healthcare Engineering, 2022.

⭐ Key Highlights

🧠 Hybrid Deep Learning Framework

🔬 U-Net Lesion Segmentation

🎨 HSV/HSL-Based Mask Generation

⚡ EfficientNetV2-S Feature Extraction

🤖 Vision Transformer Global Feature Learning

🖼️ Segmentation-Guided 4-Channel Input

⚖️ Balanced Class Sampling

🎯 Categorical Focal Crossentropy

🔄 Test-Time Augmentation

📊 Multi-Class Skin Disease Classification

📈 89.14% Reported Validation Accuracy

💻 Jupyter Notebook-Based Implementation

📜 License

This project is developed for educational and research purposes.
