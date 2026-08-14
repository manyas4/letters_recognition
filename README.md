# Real-Time Hand Gesture-Based Letter Recognition

A real-time computer vision and machine learning project that recognizes **A–Z hand gestures** using a webcam and predicts the corresponding alphabet letter.

Recognized letters can be entered sequentially to form words or sentences. Basic keyboard controls are provided to add spaces, delete characters, and clear the generated text.

> **Note:** This project recognizes predefined A–Z hand gestures. It is not a complete sign-language translation system.

---

## Features

- Real-time A–Z hand gesture recognition
- Webcam-based input using OpenCV
- Hand landmark detection using MediaPipe
- 21 hand landmarks used for feature extraction
- 63 numerical hand-landmark features
- Random Forest classifier for letter prediction
- Prediction smoothing for stable recognition
- Letter locking to prevent repeated predictions
- Sequential letter input for creating words and sentences
- Keyboard controls for space, backspace, and clearing text
- A–Z gesture reference chart

---

## Technologies Used

- **Python**
- **OpenCV** – webcam capture and image processing
- **MediaPipe** – hand landmark detection
- **NumPy** – numerical computations
- **Pandas** – dataset handling
- **Scikit-learn** – machine learning
- **Random Forest Classifier** – letter classification
- **Joblib** – model saving and loading

---

## How It Works

```text
Webcam
   ↓
Hand Detection using MediaPipe
   ↓
21 Hand Landmarks
   ↓
63 Landmark Features
   ↓
Random Forest Classifier
   ↓
Predicted A–Z Letter
   ↓
Prediction Smoothing
   ↓
Letter Locking
   ↓
Text Output
```

### 1. Hand Detection

The webcam captures live video frames and MediaPipe detects the user's hand and its 21 landmarks.

### 2. Feature Extraction

The x, y, and z coordinates of the 21 hand landmarks are used as numerical features.

This produces:

**21 × 3 = 63 features**

### 3. Letter Prediction

The extracted features are passed to a trained Random Forest classifier, which predicts the corresponding alphabet letter.

### 4. Prediction Smoothing

Recent predictions are stored and used to obtain a more stable prediction, reducing fluctuations between consecutive video frames.

### 5. Letter Locking

Once a letter is recognized, the system locks the prediction to prevent the same gesture from being repeatedly added while the hand remains in position.

The user can remove their hand before entering the next letter.

### 6. Text Construction

Recognized letters are added sequentially to the output.

For example:

```text
H → E → L → L → O

Output:
HELLO
```

Keyboard controls can then be used to edit the generated text.

---

## Project Structure

```text
MinorProject/
│
├── Data/
│   └── h_g_d_letters.csv
│
├── Models/
│   └── gesture_model_letters.pkl
│
├── pro_letters.py
├── train_letters.py
├── datacollection_letters.py
├── letters.jpeg
└── README.md
```

---

## File Description

| File | Description |
|------|-------------|
| `pro_letters.py` | Main application for real-time A–Z gesture recognition |
| `train_letters.py` | Trains the Random Forest letter classification model |
| `datacollection_letters.py` | Collects training data for A–Z gestures |
| `h_g_d_letters.csv` | Dataset containing hand-landmark features and labels |
| `gesture_model_letters.pkl` | Trained Random Forest model |
| `letters.jpeg` | A–Z gesture reference image |
| `README.md` | Project documentation |

---

## Installation

Clone the repository:

```bash
git clone <your-repository-url>
cd MinorProject
```

Install the required dependencies:

```bash
pip install opencv-python mediapipe numpy pandas scikit-learn joblib
```

---

## Run the Application

Make sure the trained model is available at:

```text
Models/gesture_model_letters.pkl
```

Run the main application:

```bash
python pro_letters.py
```

The application will open the webcam and start recognizing A–Z hand gestures.

---

## Keyboard Controls

| Key | Function |
|-----|----------|
| `SPACE` | Add a space |
| `BACKSPACE` | Delete the last character |
| `C` | Clear the generated text |
| `Q` | Quit the application |

---

## Training the Model

### Collect Training Data

To collect your own A–Z gesture dataset, run:

```bash
python datacollection_letters.py
```

The collected data is stored in:

```text
Data/h_g_d_letters.csv
```

### Train the Model

After collecting the required data, train the Random Forest classifier using:

```bash
python train_letters.py
```

The trained model is saved as:

```text
Models/gesture_model_letters.pkl
```

---

## Purpose

The project demonstrates how **computer vision and machine learning** can be combined to create a real-time, touch-free method of entering alphabet characters.

The system can be used for:

- Touch-free text input
- Human-computer interaction
- Computer vision demonstrations
- Machine learning experimentation
- Accessibility-oriented interfaces

---

## Limitations

- The system recognizes only the predefined A–Z gestures included in the training dataset.
- Recognition performance can be affected by lighting, camera quality, hand position, and background conditions.
- The system recognizes individual predefined gestures rather than interpreting complete sign language.
- Dynamic gestures and continuous hand movements are not specifically modeled.
- The project is a gesture-recognition prototype and not a complete sign-language translation system.

---

## Future Improvements

- Improve recognition accuracy using a larger and more diverse dataset
- Support different hand orientations and lighting conditions
- Add dynamic gesture recognition
- Add number recognition
- Add text-to-speech functionality
- Improve the user interface
- Add support for multiple hands
- Integrate language-based text correction

---

## Author

**Manya Singh**

Computer Science Engineering Student
