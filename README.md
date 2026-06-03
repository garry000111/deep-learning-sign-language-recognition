# deep-learning-sign-language-recognition
Real-time Sign Language Recognition System using MediaPipe Holistic, OpenCV, and LSTM networks for gesture classification from live webcam streams.

This project focuses on recognizing sign language gestures in real-time using computer vision and deep learning techniques. The workflow includes collecting gesture data using a webcam, extracting body and hand landmarks with MediaPipe Holistic, building sequences of keypoints, and training an LSTM-based neural network to classify sign language actions.

The project was developed as an end-to-end deep learning application, covering data collection, preprocessing, model training, evaluation, and real-time inference.

## **About the Dataset**

The dataset used in this project was custom-created using a webcam and MediaPipe Holistic. For each sign language action, landmark coordinates from the face, pose, and both hands were extracted and stored as NumPy arrays.

### Actions Collected

1. **Hello**
2. **Thanks**
3. **I Love You**

### Dataset Structure

For each action:

* **30 sequences (videos)**
* **30 frames per sequence**
* **1662 keypoints per frame**

Each frame contains:

1. **Pose Landmarks**

   * 33 landmarks
   * (x, y, z, visibility)

2. **Face Landmarks**

   * 468 landmarks
   * (x, y, z)

3. **Left Hand Landmarks**

   * 21 landmarks
   * (x, y, z)

4. **Right Hand Landmarks**

   * 21 landmarks
   * (x, y, z)

These landmarks are extracted using MediaPipe Holistic and stored as feature vectors for model training.

---

## **Project Overview**

### 1. Data Collection

* **Webcam Data Acquisition:** Captured real-time gesture videos using OpenCV.
* **Landmark Extraction:** Used MediaPipe Holistic to extract face, pose, and hand landmarks.
* **Sequence Generation:** Stored landmark coordinates for multiple frames to capture temporal information.

### 2. Visualization

* **Real-Time Landmark Detection:** Displayed detected face, pose, and hand landmarks on live webcam feed.
* **Gesture Collection Interface:** Implemented a data collection pipeline with visual prompts for recording gestures.
* **Landmark Visualization:** Visualized keypoint connections for hands, pose, and face using MediaPipe drawing utilities.

### 3. Feature Engineering

* **Keypoint Extraction:** Converted detected landmarks into numerical feature vectors.
* **Sequence Creation:** Combined multiple consecutive frames into fixed-length sequences.
* **Missing Landmark Handling:** Replaced missing landmarks with zero vectors to maintain consistent input dimensions.
* **Data Formatting:** Structured data for sequence-based deep learning models.

### 4. Modeling

#### Deep Learning Model

The model was built using TensorFlow/Keras and consists of:

* LSTM Layer (64 units)
* LSTM Layer (128 units)
* LSTM Layer (64 units)
* Dense Layer (64 units)
* Dense Layer (32 units)
* Output Layer (Softmax)

The model learns temporal patterns from sequences of body and hand movements to classify sign language gestures.

### 5. Model Evaluation

The model is evaluated using:

* Accuracy
* Loss Curves
* Confusion Matrix
* Real-Time Prediction Performance

Predictions are generated from live webcam streams and displayed with confidence scores.

### 6. Real-Time Inference

* Captures video frames from webcam.
* Extracts landmarks using MediaPipe Holistic.
* Builds sequences of keypoints.
* Feeds sequences into the trained LSTM model.
* Displays predicted sign language gesture in real-time.

---

## **Technologies Used**

* Python
* OpenCV
* MediaPipe Holistic
* NumPy
* TensorFlow / Keras
* Scikit-Learn
* Matplotlib

---

## **Project Workflow**

1. Collect Sign Language Data
2. Extract MediaPipe Landmarks
3. Store Keypoints as NumPy Arrays
4. Create Action Sequences
5. Train LSTM Model
6. Evaluate Model Performance
7. Deploy Real-Time Prediction System

---

## **Future Improvements**

* Increase the number of supported gestures.
* Add sentence-level sign language recognition.
* Implement attention-based architectures.
* Deploy as a web application using Streamlit.
* Integrate text-to-speech functionality for improved accessibility.
