Draw in the air with your fingertips — no mouse, no pen, just pure magic! ✨
🚀 Live Demo • 📦 Installation • 🎯 Features • 📖 Documentation
</div>

🌟 Introduction
Welcome to AI Virtual Painter — a real-time computer vision application that transforms your hand into a digital brush! Using cutting-edge hand tracking technology, this project enables you to create art in mid-air with intuitive gesture controls. Whether you're sketching ideas during a presentation, creating digital art for fun, or exploring the intersection of AI and creativity, Virtual Painter makes it effortless and magical.
The Magic Behind It:

🖐️ Natural Gestures: Your hand movements are tracked in real-time with 21 precise landmarks
🎨 Intuitive Controls: Two simple hand gestures control everything — selection and drawing
⚡ Real-Time Performance: Smooth, lag-free drawing experience at 30+ FPS
🌐 Cross-Platform: Available as both a Python desktop app and a web application


🎯 Key Features
🚀 Core Capabilities
FeatureDescriptionReal-Time Hand TrackingPowered by MediaPipe's ML models, tracking 21 hand landmarks at 30+ FPSDual Mode SystemSwitch seamlessly between Selection Mode and Drawing Mode using finger gesturesColor PaletteChoose from multiple vibrant colors with a simple gestureSmart EraserTrue erasing effect (not just painting in white!) using canvas composite operationsMirrored DisplayIntuitive mirror-mode camera feed for natural movement coordinationPersistent CanvasYour drawings remain on screen even when your hand moves awayVisual FeedbackLive hand skeleton visualization with green connectors and red joint markers
🎨 Drawing Modes
Selection Mode 🖐️

Trigger: Index finger + Middle finger both extended
Action: Move your hand over the color header to select colors or the eraser
Visual: Hand skeleton visible, no drawing occurs

Drawing Mode ✍️

Trigger: Only Index finger extended
Action: Draw freely on the canvas with your selected color
Visual: Hand skeleton visible, drawing trail follows your fingertip

🌈 Available Colors

🔵 Blue (Default)
💚 Green
❤️ Red
💛 Yellow
🧽 Eraser (True transparency using destination-out composite)


🛠️ Tech Stack
Desktop Version (Python)
┌─────────────────────────────────────────┐
│  Hand Tracking       MediaPipe Hands    │
│  Computer Vision     OpenCV (cv2)       │
│  Array Operations    NumPy              │
│  Canvas Merging      Bitwise Operations │
└─────────────────────────────────────────┘
Web Version (JavaScript)
┌─────────────────────────────────────────┐
│  Hand Tracking       MediaPipe Hands API│
│  Canvas Rendering    HTML5 Canvas       │
│  Styling             CSS3 + Glow FX     │
│  Eraser Logic        globalComposite-   │
│                      Operation           │
└─────────────────────────────────────────┘
Technical Highlights
Python Implementation:

Dynamic header overlay system using image blending
Bitwise cv2.addWeighted() operations for smooth canvas merging
Optimized frame processing pipeline for minimal latency
Custom hand landmark distance calculations for gesture recognition

Web Implementation:

Navy Blue UI theme with frosted glass effects
CSS backdrop blur filters for modern aesthetics
destination-out composite mode for true pixel erasing
Responsive design that adapts to different screen sizes
Mirrored video feed using transform: scaleX(-1) for intuitive interaction


📦 Installation
Python Version
Prerequisites

Python 3.8 or higher
Webcam (built-in or external)

Step 1: Clone the Repository
bashgit clone https://github.com/yourusername/ai-virtual-painter.git
cd ai-virtual-painter
Step 2: Install Dependencies
bashpip install opencv-python mediapipe numpy
Or use the requirements file:
bashpip install -r requirements.txt
Step 3: Set Up Header Images
Create a Header folder in the project root and add your color selection images:
ai-virtual-painter/
├── Header/
│   ├── 1.png    # Blue
│   ├── 2.png    # Green
│   ├── 3.png    # Red
│   ├── 4.png    # Yellow
│   └── 5.png    # Eraser
├── virtual_painter.py
└── requirements.txt
Header Image Specifications:

Dimensions: 1280 x 125 pixels (recommended)
Format: PNG with transparency
Layout: 5 equal sections (one for each color/eraser)

Step 4: Run the Application
bashpython virtual_painter.py
Press q to quit the application.

Web Version
🌐 Live Demo
👉 Try it now in your browser! (No installation required)
Local Setup

Clone the repository (same as above)
Navigate to the web directory:

bash   cd web

Open index.html in a modern browser (Chrome/Edge recommended)

bash   # On macOS:
   open index.html
   
   # On Windows:
   start index.html
   
   # On Linux:
   xdg-open index.html

Allow camera permissions when prompted

Note: Web version requires an HTTPS connection or localhost for camera access.

📖 Usage Guide
Getting Started

Launch the Application

Python: Run python virtual_painter.py
Web: Open index.html in your browser


Position Yourself

Sit 2-3 feet away from your webcam
Ensure good lighting for optimal hand tracking
Your hand should be clearly visible in the frame


Understand the Hand Landmarks

The system tracks 21 points on your hand
Fingertip positions: Index = Landmark 8, Middle = Landmark 12
Green lines = connections between landmarks
Red dots = individual joint positions



Gesture Controls
✌️ Selection Mode (Choose Colors)
How to activate:

Extend both your index finger and middle finger
Keep other fingers closed
Move your hand over the color header at the top of the screen

What happens:

Your fingertip acts as a cursor
Hovering over a color section selects that color
The selected color becomes active for drawing
No drawing occurs in this mode

☝️ Drawing Mode (Create Art)
How to activate:

Extend only your index finger
Keep all other fingers closed (including middle finger)
Move your hand to draw

What happens:

A trail follows your index fingertip
Lines are drawn in your selected color
The canvas persists even when you stop drawing
Move smoothly for clean lines

🧽 Using the Eraser
Python Version:

Select the eraser from the header (rightmost section)
Draw in "white" to cover previous strokes

Web Version (Advanced):

Select the eraser from the header
Uses globalCompositeOperation = 'destination-out'
Actually removes pixels from the canvas (true transparency!)
Creates authentic erasing effect, not just white paint

Pro Tips for Best Results
TipDescription🌟 Smooth MovementsMove slowly and steadily for cleaner lines💡 Good LightingBright, even lighting improves hand detection accuracy🎯 Steady HandsRest your elbow on a surface to reduce jitter📏 Optimal DistanceStay 2-3 feet from camera for best tracking🖐️ Clear GesturesMake distinct finger positions for reliable mode switching🔄 Mirror ModeWeb version mirrors the feed — move right hand right to draw right!

🧠 How It Works
The Magic Under the Hood
1. Hand Detection Pipeline
Camera Feed → MediaPipe Model → 21 Landmark Coordinates → Gesture Recognition
MediaPipe Hands uses machine learning to detect:

Hand presence in frame
21 3D coordinates (x, y, z) for each hand landmark
Hand orientation and finger states

2. Gesture Recognition Logic
Finger State Detection:
python# Simplified pseudo-code
index_up = landmarks[8].y < landmarks[6].y
middle_up = landmarks[12].y < landmarks[10].y

if index_up and middle_up:
    mode = "SELECTION"
elif index_up and not middle_up:
    mode = "DRAWING"
else:
    mode = "IDLE"
Why this works:

Landmark 8 = Index fingertip
Landmark 6 = Index middle joint
If fingertip Y-coordinate < joint Y-coordinate = finger is extended
Same logic applies to all fingers

3. Canvas Management
Python Version:
python# Create persistent canvas
canvas = np.zeros((480, 640, 3), np.uint8)

# Draw on canvas when in drawing mode
if mode == "DRAWING":
    cv2.circle(canvas, (x, y), brushSize, color, cv2.FILLED)

# Merge canvas with live feed
result = cv2.addWeighted(frame, 0.7, canvas, 0.3, 0)
Web Version:
javascript// Set drawing mode
if (isDrawing) {
    ctx.globalCompositeOperation = 'source-over'; // Normal drawing
    ctx.strokeStyle = currentColor;
} else if (isErasing) {
    ctx.globalCompositeOperation = 'destination-out'; // True erasing
}

// Draw on persistent canvas
ctx.lineTo(x, y);
ctx.stroke();
4. The Eraser Technology
Standard Approach (Python):

Draws in white/black color
Covers but doesn't remove previous pixels
Limited to opaque backgrounds

Advanced Approach (Web):
javascriptctx.globalCompositeOperation = 'destination-out';

destination-out: Removes pixels where new drawing occurs
Creates actual transparency in the canvas
Allows you to "see through" erased areas
More intuitive and realistic erasing experience

5. Visual Feedback System
Hand Skeleton Rendering:
python# Draw connections (green lines)
for connection in HAND_CONNECTIONS:
    cv2.line(frame, landmark1, landmark2, (0, 255, 0), 2)

# Draw landmarks (red dots)
for landmark in landmarks:
    cv2.circle(frame, (x, y), 5, (0, 0, 255), cv2.FILLED)
This provides instant visual confirmation that your hand is being tracked correctly.

🎨 UI/UX Design
Python Version Design
Header System:

Fixed 125px height header bar at top
5 equal sections (each 256px wide for 1280px total)
PNG images with transparency for modern look
Bitwise operations blend header with video feed

Color Scheme:

Section 1: Blue (#0000FF)
Section 2: Green (#00FF00)
Section 3: Red (#FF0000)
Section 4: Yellow (#FFFF00)
Section 5: Eraser (represented by white/gray icon)

Canvas Blending:
pythonalpha = 0.7  # Video feed weight
beta = 0.3   # Canvas weight
merged = cv2.addWeighted(frame, alpha, canvas, beta, 0)

Creates semi-transparent drawing overlay
Maintains visibility of video feed
Professional, non-intrusive visual style

Web Version Design
Modern Aesthetic:

🌊 Navy Blue Theme: background: linear-gradient(135deg, #1a1a2e, #16213e)
✨ Glassmorphism: Frosted glass effect on UI panels
💫 Glow Effects: Subtle box-shadows for depth
🔄 Mirrored Feed: transform: scaleX(-1) for natural interaction

CSS Highlights:
css.video-container {
    backdrop-filter: blur(10px);
    background: rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

.color-button {
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.color-button:hover {
    transform: translateY(-5px) scale(1.05);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}
Responsive Layout:

Flexbox-based responsive grid
Adapts to different screen sizes
Touch-friendly button sizes (minimum 44x44px)
Mobile-first design principles


🔮 Future Roadmap
Planned Features

 Basic hand tracking and drawing
 Color selection system
 True eraser functionality (Web)
 🖼️ Save to PNG: Export your artwork as downloadable images
 🎤 Voice Commands: "Draw in blue", "Switch to eraser", "Clear canvas"
 👐 Multi-Hand Support: Draw with both hands simultaneously
 🖌️ Brush Styles: Different brush sizes, spray paint, pencil textures
 ↩️ Undo/Redo: Navigate through your drawing history
 🎨 Custom Color Picker: RGB/HSV color selection with gradient UI
 📱 Mobile App: Native iOS/Android applications
 🤝 Collaborative Mode: Real-time multi-user drawing sessions
 🎬 Recording Mode: Create time-lapse videos of your drawing process
 🧠 Gesture Shortcuts: Custom gestures for common actions
 🌈 Gradient Brushes: Multi-color brush effects
 📐 Shape Tools: Circles, rectangles, lines with gesture controls

Performance Optimizations

 GPU acceleration for MediaPipe inference
 WebGL-based canvas rendering for smoother performance
 Optimized landmark smoothing algorithms
 Adaptive quality based on system performance


🏗️ Project Structure
ai-virtual-painter/
│
├── 📁 Header/                 # Color selection header images
│   ├── 1.png                  # Blue color
│   ├── 2.png                  # Green color
│   ├── 3.png                  # Red color
│   ├── 4.png                  # Yellow color
│   └── 5.png                  # Eraser
│
├── 📁 web/                    # Web version files
│   ├── index.html             # Main HTML structure
│   ├── styles.css             # Navy blue theme & animations
│   ├── script.js              # MediaPipe + Canvas logic
│   └── assets/                # Additional resources
│
├── 📁 docs/                   # Documentation
│   ├── SETUP.md               # Detailed setup instructions
│   ├── API.md                 # Code documentation
│   └── CONTRIBUTING.md        # Contribution guidelines
│
├── virtual_painter.py         # Python main application
├── requirements.txt           # Python dependencies
├── README.md                  # This file
└── LICENSE                    # MIT License

🤝 Contributing
Contributions are what make the open-source community such an amazing place to learn, inspire, and create! Any contributions you make are greatly appreciated.
How to Contribute

Fork the Project

bash   git clone https://github.com/yourusername/ai-virtual-painter.git

Create your Feature Branch

bash   git checkout -b feature/AmazingFeature

Commit your Changes

bash   git commit -m 'Add some AmazingFeature'

Push to the Branch

bash   git push origin feature/AmazingFeature

Open a Pull Request

Contribution Ideas

🐛 Bug Fixes: Found a bug? Fix it and submit a PR!
✨ New Features: Implement features from the roadmap
📝 Documentation: Improve or translate documentation
🎨 UI/UX: Enhance the visual design and user experience
⚡ Performance: Optimize code for better speed
🧪 Testing: Add unit tests and integration tests


📜 License
This project is licensed under the MIT License - see the LICENSE file for details.
TL;DR: You can use, modify, and distribute this software freely, even for commercial purposes, as long as you include the original license.

🙏 Acknowledgments
Special Thanks To:

Google MediaPipe - For the incredible hand tracking ML models
OpenCV - For powerful computer vision tools
NumPy - For efficient array operations
Hack Club Community - For inspiration and support
Open Source Contributors - For making this project possible

Inspiration
This project was inspired by:

The intersection of AI and creative expression
Natural user interfaces and gesture-based computing
Accessibility in digital art tools
The magic of turning code into interactive experiences


📞 Contact & Support
Get in Touch

Email: kwael6774@gmail.com
GitHub Issues: Report a bug or request a feature
Discussions: Join the conversation

Support This Project
If you found this project helpful or inspiring:

⭐ Star this repository
🐦 Share on social media
💬 Spread the word in your community
🛠️ Contribute code or ideas


🎓 Educational Use
This project is perfect for:

🏫 Computer Vision Courses: Practical example of hand tracking
🤖 AI/ML Workshops: Real-world MediaPipe application
👨‍💻 Coding Bootcamps: Interactive Python/JavaScript project
🧑‍🎓 Student Projects: Portfolio-ready open-source contribution
📚 Self-Learning: Comprehensive, well-documented codebase


📊 Technical Specifications
SpecificationPython VersionWeb VersionMinimum FPS25-3030+Latency< 50ms< 30msResolution640x480 (default)AdaptiveLandmarks Tracked21 per hand21 per handSupported BrowsersN/AChrome 90+, Edge 90+Python Version3.8+N/AMemory Usage~200MB~150MBCamera Requirements720p recommended720p recommended

🐛 Troubleshooting
Common Issues
Issue: Hand not being detected

✅ Ensure good lighting conditions
✅ Keep hand at 2-3 feet from camera
✅ Make sure fingers are clearly separated
✅ Check camera permissions in browser (Web version)

Issue: Drawing is laggy

✅ Close other applications to free up CPU
✅ Reduce video resolution in code
✅ Update graphics drivers
✅ Use a dedicated GPU if available

Issue: Colors not changing

✅ Verify Header images are in correct folder
✅ Check that both index and middle fingers are up
✅ Hover over header area slowly

Issue: Eraser not working properly (Web)

✅ Clear browser cache
✅ Use latest Chrome/Edge browser
✅ Ensure JavaScript is enabled

Getting Help

Check the FAQ
Search existing issues
Open a new issue with:

System information (OS, Python/Browser version)
Steps to reproduce
Screenshots/videos if possible




🌟 Showcase
Gallery
Add your creations here! Submit a PR to feature your artwork.
<!-- Placeholder for user-submitted artwork -->

<div align="center">
💝 Made with Love and Code
If this project helped you or inspired you, consider giving it a ⭐!
Happy Drawing! 🎨✨
"Art is not what you see, but what you make others see." — Edgar Degas