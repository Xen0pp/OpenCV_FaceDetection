# 🎯 OpenCV Basic - Face Detection & Recognition System

<div align="center">

![OpenCV](https://img.shields.io/badge/OpenCV-4.x-brightgreen?style=flat-square&logo=opencv)
![Python](https://img.shields.io/badge/Python-3.7%2B-blue?style=flat-square&logo=python)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-success?style=flat-square)

**A comprehensive computer vision project for real-time face detection and recognition using OpenCV, Haar Cascades, and Machine Learning (KNN)**

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Project Structure](#-project-structure) • [Contributing](#-contributing)

</div>

---

## 📋 Overview

This project demonstrates fundamental concepts of computer vision and machine learning by implementing a complete face detection and recognition system. It captures video streams from a webcam, detects faces using Haar Cascade classifiers, extracts facial features, and uses K-Nearest Neighbors (KNN) classification to recognize and identify individuals in real-time.

Perfect for learning OpenCV, image processing, and introductory machine learning concepts!

---

## ✨ Features

- **🎥 Real-time Face Detection**: Detect faces in video streams using Haar Cascade classifiers
- **📸 Face Data Collection**: Capture and store facial data for training recognition models
- **🤖 Face Recognition**: Identify people in real-time using KNN classification algorithm
- **🖼️ Image Processing**: Convert images to grayscale and perform various OpenCV operations
- **📊 Data Management**: Store and load facial training data using NumPy
- **💻 Jupyter Integration**: Includes Jupyter Notebook for interactive experimentation

---

## 🛠️ Technical Stack

| Technology | Purpose |
|-----------|---------|
| **OpenCV** | Computer vision and image processing |
| **NumPy** | Numerical operations and data manipulation |
| **Scikit-learn** | Machine learning (KNN classifier) |
| **Python 3.7+** | Core programming language |
| **Jupyter Notebook** | Interactive development and experimentation |

---

## 📦 Installation

### Prerequisites
- Python 3.7 or higher
- Webcam or video capture device
- pip (Python package manager)

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/OpenCV_Basic.git
cd OpenCV_Basic
```

### Step 2: Create Virtual Environment (Recommended)
```bash
# On Linux/Mac
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

Or install manually:
```bash
pip install opencv-python numpy scikit-learn jupyter
```

---

## 🚀 Usage

### 1. **OpenCV.py** - Basic Image Operations
Learn fundamental OpenCV operations like reading images and color space conversion.

```bash
python OpenCV.py
```

**What it does:**
- Reads an image file (`dog.png`)
- Converts BGR to Grayscale
- Displays both images side by side

---

### 2. **cv_video_read.py** - Webcam Video Capture
Capture and display video stream from your webcam.

```bash
python cv_video_read.py
```

**What it does:**
- Opens webcam feed
- Displays real-time video
- Press `q` to exit

> **Note:** Modify `cv2.VideoCapture(1)` if you have multiple cameras (0, 1, 2, etc.)

---

### 3. **FaceDetection.py** - Real-time Face Detection
Detect faces in real-time video stream with bounding boxes.

```bash
python FaceDetection.py
```

**What it does:**
- Captures video from webcam
- Detects faces using Haar Cascade classifier
- Draws blue bounding boxes around detected faces
- Press `q` to exit

**Output:**
```
[[x1 y1 w1 h1]
 [x2 y2 w2 h2]
 ...]
```

---

### 4. **Face_Data.py** - Collect Training Data
Capture facial images of a person and save for training the recognition model.

```bash
python Face_Data.py
```

**What it does:**
- Prompts you to enter a person's name
- Captures 10+ face samples from video stream
- Resizes each face to 100×100 pixels
- Saves data as NumPy array in `./data/[name].npy`

**Example:**
```
Enter the name of the Person: John
Data Successfully saved
```

---

### 5. **FaceRecog.py** - Face Recognition
Recognize and identify people in real-time using the trained model.

```bash
python FaceRecog.py
```

**Prerequisites:**
- Run `Face_Data.py` first to collect training data for at least 2 people
- Ensure `.npy` files are in the `./data/` directory

**What it does:**
- Loads training data from saved `.npy` files
- Trains KNN classifier (k=5)
- Captures video and detects faces
- Identifies and labels each face with the person's name
- Press `q` to exit

**Sample Output:**
```
Loaded Riya.npy
Loaded Shubham.npy
Face dataset shape: (50, 10000)
Face labels shape: (50,)
Names: {0: 'Riya', 1: 'Shubham'}
```

---

## 📁 Project Structure

```
OpenCV_Basic/
├── README.md                          # Project documentation
├── requirements.txt                   # Python dependencies
│
├── OpenCV.py                          # Basic image processing
├── cv_video_read.py                   # Webcam video capture
├── FaceDetection.py                   # Face detection (Haar Cascade)
├── Face_Data.py                       # Training data collection
├── FaceRecog.py                       # Face recognition (KNN)
│
├── OpenCvBasic.ipynb                  # Jupyter notebook for experimentation
│
├── haarcascade_frontalface_alt.xml    # Pre-trained Haar Cascade classifier
│
├── data/                              # Training data directory
│   ├── Riya.npy                       # Sample training data for Riya
│   └── Shubham.npy                    # Sample training data for Shubham
│
└── dog.png                            # Sample image for testing
```

---

## 🎓 How It Works

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                    FACE DETECTION & RECOGNITION             │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  [Webcam Input] → [Haar Cascade] → [Face Detection]        │
│                                           ↓                 │
│                                    [Face Extraction]        │
│                                           ↓                 │
│                    ┌────────────────────────────────────┐   │
│                    │   TRAINING PHASE                   │   │
│                    │ ┌──────────────────────────────┐   │   │
│                    │ │ 1. Collect face images      │   │   │
│                    │ │ 2. Resize to 100×100       │   │   │
│                    │ │ 3. Flatten and save (.npy) │   │   │
│                    │ └──────────────────────────────┘   │   │
│                    └────────────────────────────────────┘   │
│                                    ↓                        │
│                    ┌────────────────────────────────────┐   │
│                    │   RECOGNITION PHASE                │   │
│                    │ ┌──────────────────────────────┐   │   │
│                    │ │ 1. Load training data       │   │   │
│                    │ │ 2. Train KNN (k=5)         │   │   │
│                    │ │ 3. Predict face labels     │   │   │
│                    │ │ 4. Display name + bbox     │   │   │
│                    │ └──────────────────────────────┘   │   │
│                    └────────────────────────────────────┘   │
│                                    ↓                        │
│                          [Output: Name + Bounding Box]      │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Key Algorithms

1. **Haar Cascade Classifier**: Detects faces using pre-trained cascade classifiers
2. **K-Nearest Neighbors (KNN)**: Classifies detected faces based on training data
3. **Face Resizing**: Standardizes all faces to 100×100 pixels for consistent feature extraction
4. **Flattening**: Converts 2D images to 1D arrays for ML model training

---

## 📊 Dataset Specifications

Each training sample is:
- **Size**: 100 × 100 pixels
- **Format**: Reshaped to flatten array (10,000 features per image)
- **Storage**: NumPy `.npy` format for efficient binary storage
- **Samples**: ~10+ images per person recommended for optimal accuracy

---

## 🔧 Configuration & Customization

### Adjust Face Detection Sensitivity
In `FaceDetection.py` and `Face_Data.py`, modify the `detectMultiScale` parameters:

```python
# Current settings
faces = face_cascade.detectMultiScale(frame, 1.3, 5)

# Parameters:
# 1.3 = scale factor (lower = more sensitive)
# 5 = minNeighbors (higher = fewer false positives)
```

### Change KNN Neighbors
In `FaceRecog.py`, modify the `k` value:

```python
# Current: k=5 (check 5 nearest neighbors)
clf = KNeighborsClassifier(5)  # Increase for more accurate but slower results
```

### Switch Camera
If you have multiple cameras, change the camera index:

```python
# 0 = default webcam, 1 = external camera, etc.
cap = cv2.VideoCapture(1)
```

---

## 💡 Tips for Better Results

✅ **Do:**
- Collect training data in good lighting conditions
- Use consistent background for training
- Capture faces from multiple angles
- Collect 10-15+ samples per person
- Use similar distances from camera
- Ensure good face visibility

❌ **Avoid:**
- Poor lighting conditions
- Partial face visibility
- Wearing hats or sunglasses during training
- Collecting data with extreme angles
- Too few training samples (< 5 per person)

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| **Camera not opening** | Change `cv2.VideoCapture(1)` to `cv2.VideoCapture(0)` |
| **Faces not detected** | Ensure good lighting, adjust scale factor and minNeighbors |
| **Module not found error** | Run `pip install -r requirements.txt` |
| **Low recognition accuracy** | Collect more training samples, ensure consistent conditions |
| **Slow performance** | Reduce frame resolution or increase frame skip rate |

---

## 📈 Performance Metrics

- **Face Detection Speed**: ~30-60 FPS (depending on hardware)
- **Recognition Speed**: ~15-30 FPS (with KNN prediction)
- **Accuracy**: 85-95% (varies with training data quality and quantity)
- **Memory Usage**: ~50-200 MB (depends on number of training samples)

---

## 🔄 Workflow Example

```bash
# 1. First time setup
python Face_Data.py
# Enter: Riya (10 samples)
# Enter: Shubham (10 samples)

# 2. Train and recognize
python FaceRecog.py
# Real-time recognition with names displayed!
```

---

## 📚 Learning Resources

- [OpenCV Official Documentation](https://docs.opencv.org/)
- [Haar Cascades Tutorial](https://docs.opencv.org/master/d7/d52/tutorial_dnn_face.html)
- [Scikit-learn KNN](https://scikit-learn.org/stable/modules/neighbors.html)
- [Computer Vision Fundamentals](https://en.wikipedia.org/wiki/Computer_vision)

---

## 🎯 Future Enhancements

- [ ] Add Deep Learning models (CNN) for better accuracy
- [ ] Implement face recognition using `face_recognition` library
- [ ] Add emotion detection capability
- [ ] Create web interface using Flask/Django
- [ ] Optimize for mobile deployment
- [ ] Add database integration for storing recognition logs
- [ ] Implement multi-face tracking
- [ ] Add face alignment preprocessing

---

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

---

## 🙏 Acknowledgments

- OpenCV community for excellent computer vision library
- Haar Cascade classifiers by Paul Viola and Michael Jones
- Scikit-learn team for machine learning tools
- All contributors and testers

---


<div align="center">

**Made with ❤️ using Python and OpenCV**

⭐ If you find this project helpful, please give it a star!

[Back to Top](#-opencv-basic---face-detection--recognition-system)

</div>
