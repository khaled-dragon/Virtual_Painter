# AI Virtual Painter 🎨✋

An AI-powered virtual painting application that allows users to draw on the screen using hand gestures captured through a camera.

## 🚀 Features
* **Gesture-Based Drawing:** Draw on the screen using your index finger detected by AI hand tracking.
* **Color Selection Mode:** Raise both index and middle fingers to switch between different colors.
* **Eraser Tool:** Select black color to erase drawings naturally.
* **Real-time Hand Tracking:** Accurate and smooth tracking using MediaPipe.
* **Dual Versions:** 
  - Desktop version using Python.
  - Web-based version using JavaScript and MediaPipe Hands.

## 🛠️ Built With
### Desktop Version
* **Python**
* **OpenCV:** For video capture and image processing.
* **MediaPipe:** For real-time hand landmark detection.
* **NumPy:** For canvas and image manipulation.

### Web Version
* **HTML / CSS / JavaScript**
* **MediaPipe Hands (Web):** Hand tracking in the browser.
* **Canvas API:** For drawing and rendering.

## 📦 Installation & Setup (Python Version)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YourUsername/AI-Virtual-Painter.git
   cd AI-Virtual-Painter

2. **Install dependencies:**
   ```bash
pip install opencv-python mediapipe numpy

3. **Run the application:**
   ```bash
   python VirtualPainter.py

## 🌐 Run Web Version

1. Make sure the **Header** folder exists and contains the header images.
2. Open `index.html` using **Live Server** or any local server.
3. Allow camera access when prompted by the browser.

---

## 🎮 How to Use

1. Show your hand clearly in front of the camera.

### 🟡 Selection Mode
- Raise your **Index** and **Middle** fingers.
- Move your hand to the **top bar** to select colors or the eraser.

### ✏️ Drawing Mode
- Raise only your **Index finger** to start drawing.
- Move your finger smoothly to paint on the screen in real time.

---

## 📁 Project Structure

```text
├── VirtualPainter.py
├── HandTrackingModule.py
├── index.html
├── Header/
│   ├── 1.png
│   ├── 2.png
│   ├── 3.png
│   └── 4.png
