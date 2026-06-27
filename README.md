# Handwritten-Digit-Recognition-System
A machine learning–based application that recognizes handwritten digits (0–9) using a Convolutional Neural Network (CNN). Built with Python, PyTorch, and Streamlit, with SQL integration for storing prediction results.

Table of Contents
Overview
Features
Tech Stack
Project Architecture
Model Details
Installation
Usage
Database Schema
Results
Future Improvements

Overview
This project solves the classic computer vision problem of recognizing handwritten digits. Users can either draw a digit directly on the canvas or upload an image, and the system predicts the digit in real time using a trained CNN model.
The application also stores every prediction result along with user data in a SQL database, enabling analysis over time.

Features
Real-time digit prediction (0–9)
Interactive drawing canvas powered by Streamlit
Image upload support for external digit images
CNN model trained on a labeled digit dataset
SQL database integration for storing prediction history
High accuracy on standard benchmark datasets

Tech Stack
LayerTechnologyLanguagePythonDeep LearningPyTorchUI / FrontendStreamlitDatabaseSQL (SQLite / MySQL)Model ArchitectureConvolutional Neural Network (CNN)

Project Architecture
handwritten-digit-recognition/
│
├── model/
│   ├── cnn_model.py          # CNN model definition
│   ├── train.py              # Model training script
│   └── saved_model.pth       # Trained model weights
│
├── app/
│   ├── app.py                # Streamlit application entry point
│   ├── predict.py            # Prediction logic
│   └── canvas.py             # Drawing canvas component
│
├── database/
│   ├── db_setup.py           # Database initialization
│   └── db_operations.py      # CRUD operations for predictions
│
├── utils/
│   └── preprocess.py         # Image preprocessing utilities
│
├── requirements.txt
└── README.md


Model Details

The CNN model is designed for grayscale 28×28 pixel images, following this architecture:

Input (1 × 28 × 28)
    ↓
Conv Layer 1 — 32 filters, 3×3 kernel, ReLU, MaxPooling
    ↓
Conv Layer 2 — 64 filters, 3×3 kernel, ReLU, MaxPooling
    ↓
Flatten
    ↓
Fully Connected Layer — 128 units, ReLU, Dropout
    ↓
Output Layer — 10 units (digits 0–9), Softmax

Training details:


Dataset: Labeled handwritten digit dataset (e.g., MNIST)
Loss function: Cross-Entropy Loss
Optimizer: Adam
Epochs: 10–20 (configurable)
Achieved high accuracy on the test set

Installation

Prerequisites

Python 3.8 or higher
pip
Steps

bash# 1. Clone the repository
git clone https://github.com/akanshakumari2004/handwritten-digit-recognition.git
cd handwritten-digit-recognition

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set up the database
python database/db_setup.py

# 5. Run the app
streamlit run app/app.py

requirements.txt

torch
torchvision
streamlit
streamlit-drawable-canvas
Pillow
numpy
sqlite3


Usage

Launch the app using streamlit run app/app.py
Open the local URL shown in your terminal (usually http://localhost:8501)
Option A: Draw a digit (0–9) on the canvas using your mouse or touchpad
Option B: Upload an image file of a handwritten digit
Click Predict to see the result
The predicted digit and confidence score are displayed instantly
The result is automatically saved to the database for future analysis



Database Schema

sqlCREATE TABLE predictions (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    input_type  TEXT NOT NULL,        -- 'drawn' or 'uploaded'
    predicted   INTEGER NOT NULL,     -- digit predicted (0–9)
    confidence  REAL,                 -- model confidence score
    timestamp   DATETIME DEFAULT CURRENT_TIMESTAMP
);


Results

The model achieves high accuracy in identifying digits from 0–9
Real-time prediction latency is minimal, providing a smooth user experience
Prediction history is stored persistently and can be queried for analysis



Future Improvements
 
 Add multi-digit recognition support
 Deploy the app to the cloud (Streamlit Cloud / Hugging Face Spaces)
 Add a dashboard to visualize prediction statistics from the database
 Extend to recognize alphabets (A–Z)
 Export prediction history as CSV

 ![image alt](https://github.com/akanshakumari2004/Handwritten-Digit-Recognition-System/blob/eee342eafb608450594c0aeddfe757e5ba599aab/SS1.png)

 ![image alt](https://github.com/akanshakumari2004/Handwritten-Digit-Recognition-System/blob/5d471d6995f6b9b4116337f674312939590920a0/SS2.png)

 ![image alt](https://github.com/akanshakumari2004/Handwritten-Digit-Recognition-System/blob/a6a7094da5ad307bf5a05a5c50eb4ddc05460ba4/SS3.png)

 ![image alt](https://github.com/akanshakumari2004/Handwritten-Digit-Recognition-System/blob/f039589fc44f7d9b81e0f8abf404f30e52b8fe5b/SS4.png)

 
 
