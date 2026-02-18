# 📦 Detailed Setup Guide

This guide provides step-by-step instructions for setting up the OpenCV Basic project on different operating systems.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation on Windows](#installation-on-windows)
- [Installation on macOS](#installation-on-macos)
- [Installation on Linux](#installation-on-linux)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)

---

## Prerequisites

Ensure you have the following before starting:

- **Python 3.7 or higher** ([Download](https://www.python.org/downloads/))
- **Git** ([Download](https://git-scm.com/))
- **A working webcam** (for video capture functionality)
- **Administrator privileges** (may be needed for driver installation)

### Check Python Installation

```bash
python --version
# or
python3 --version
```

---

## Installation on Windows

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/OpenCV_Basic.git
cd OpenCV_Basic
```

### Step 2: Create Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
venv\Scripts\activate
```

You should see `(venv)` in your terminal prompt, indicating the virtual environment is active.

### Step 3: Upgrade pip

```bash
python -m pip install --upgrade pip
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 5: Verify Installation

```bash
python -c "import cv2; import numpy; import sklearn; print('All libraries installed successfully!')"
```

---

## Installation on macOS

### Step 1: Install Homebrew (if not already installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Step 2: Clone the Repository

```bash
git clone https://github.com/yourusername/OpenCV_Basic.git
cd OpenCV_Basic
```

### Step 3: Create Virtual Environment

```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate
```

You should see `(venv)` in your terminal prompt.

### Step 4: Upgrade pip

```bash
python3 -m pip install --upgrade pip
```

### Step 5: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Verify Installation

```bash
python3 -c "import cv2; import numpy; import sklearn; print('All libraries installed successfully!')"
```

---

## Installation on Linux (Ubuntu/Debian)

### Step 1: Update System Packages

```bash
sudo apt-get update
sudo apt-get upgrade -y
```

### Step 2: Install Required System Dependencies

```bash
# For OpenCV
sudo apt-get install -y \
    python3-dev \
    python3-pip \
    python3-venv \
    build-essential \
    cmake \
    git \
    libopencv-dev \
    python3-opencv

# For video capture support
sudo apt-get install -y \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgomp1
```

### Step 3: Clone the Repository

```bash
git clone https://github.com/yourusername/OpenCV_Basic.git
cd OpenCV_Basic
```

### Step 4: Create Virtual Environment

```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate
```

You should see `(venv)` in your terminal prompt.

### Step 5: Upgrade pip

```bash
python3 -m pip install --upgrade pip
```

### Step 6: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 7: Verify Installation

```bash
python3 -c "import cv2; import numpy; import sklearn; print('All libraries installed successfully!')"
```

---

## Verification

### Test 1: Check Installed Packages

```bash
pip list
```

You should see:
- `opencv-python`
- `numpy`
- `scikit-learn`

### Test 2: Test OpenCV

```bash
python -c "import cv2; print(f'OpenCV Version: {cv2.__version__}')"
```

### Test 3: Test Basic Image Operations

```bash
python OpenCV.py
```

You should see a dog image and its grayscale version.

### Test 4: Test Camera Access

```bash
python cv_video_read.py
```

Press `q` to exit. You should see your webcam feed.

---

## Deactivate Virtual Environment

When you're done working on the project:

```bash
deactivate
```

---

## Reactivate Virtual Environment

To work on the project again:

**Windows:**
```bash
venv\Scripts\activate
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

---

## Troubleshooting

### Issue 1: "python: command not found"

**Solution:**
```bash
# Try using python3 instead
python3 --version

# Alias python to python3
alias python=python3
```

### Issue 2: "No module named 'cv2'"

**Solution:**
```bash
# Make sure virtual environment is activated
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate

# Reinstall OpenCV
pip install --upgrade opencv-python
```

### Issue 3: Camera Not Detected

**Windows:**
- Update camera drivers from Device Manager
- Try different camera indices: `cv2.VideoCapture(0)` or `cv2.VideoCapture(1)`

**macOS:**
- Grant camera permissions in System Preferences > Security & Privacy > Camera
- Try different camera indices

**Linux:**
```bash
# Check available cameras
v4l2-ctl --list-devices

# Install v4l-utils if needed
sudo apt-get install v4l-utils
```

### Issue 4: Permission Denied on Linux

**Solution:**
```bash
# Add user to video group
sudo usermod -a -G video $USER

# Log out and log back in for changes to take effect
```

### Issue 5: OpenCV Module Import Error

**Solution:**
```bash
# Reinstall OpenCV
pip uninstall opencv-python -y
pip install opencv-python --force-reinstall

# Or try the headless version
pip install opencv-python-headless
```

### Issue 6: Low FPS or Performance Issues

**Solution:**
- Close other applications consuming CPU
- Reduce frame resolution
- Increase the wait time in `cv2.waitKey()`
- Use GPU-accelerated OpenCV build

### Issue 7: Jupyter Notebook Issues

**Solution:**
```bash
# Install/reinstall Jupyter
pip install --upgrade jupyter

# Start Jupyter
jupyter notebook

# Select the project folder and open OpenCvBasic.ipynb
```

---

## Advanced Setup Options

### Using Conda (Alternative to venv)

```bash
# Create conda environment
conda create -n opencv_env python=3.9

# Activate environment
conda activate opencv_env

# Install dependencies
conda install -c conda-forge opencv numpy scikit-learn jupyter

# Deactivate
conda deactivate
```

### Using Docker

```bash
# Build Docker image
docker build -t opencv_basic .

# Run container with GPU support (if available)
docker run --gpus all -it opencv_basic

# Run container with volume mount
docker run -v $(pwd):/workspace -it opencv_basic
```

### GPU Acceleration (Optional)

For NVIDIA GPUs:
```bash
pip install opencv-contrib-python
# Requires CUDA Toolkit installation
```

---

## Next Steps

1. Read the [README.md](README.md) for project overview
2. Run individual scripts to understand each component
3. Collect face data using `Face_Data.py`
4. Train recognition model using `FaceRecog.py`
5. Experiment with parameters in the code
6. Refer to [CONTRIBUTING.md](CONTRIBUTING.md) if you want to contribute

---

## Getting Help

- 📖 Check [README.md](README.md) for documentation
- 🐛 Search existing [Issues](https://github.com/yourusername/OpenCV_Basic/issues)
- 📝 Create a new [Issue](https://github.com/yourusername/OpenCV_Basic/issues/new) if problem persists
- 💬 Refer to official documentation:
  - [OpenCV Docs](https://docs.opencv.org/)
  - [NumPy Docs](https://numpy.org/doc/)
  - [Scikit-learn Docs](https://scikit-learn.org/stable/documentation.html)

---

**Happy coding! 🚀**
