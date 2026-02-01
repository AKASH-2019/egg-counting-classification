# 🥚 Egg Counting & Classification System using YOLO + ByteTrack

Project URL [LINK](https://drive.google.com/drive/folders/1716zdojH_X87hSAWgxM6pmIxtiQKYg8S?usp=sharing)
### 📌 Project Overview
This project implements an automated egg detection, classification, tracking, and counting system from conveyor belt videos using Computer Vision and Deep Learning.
Eggs are detected and classified as White (cls=1) or Brown (cls=0), tracked with unique IDs, and counted only when they cross a vertical counting line to prevent duplicate counts.

### 🎯 Objectives
* Detect eggs in real-time from video streams
* Classify eggs into White and Brown
* Track each egg across frames using ByteTrack
* Count eggs accurately when crossing a defined border line
* Generate annotated videos showing egg detection and counts

### 🧠 Tech Stack
* Python 3.12+
* YOLOv8 (Ultralytics) – Object Detection
* ByteTrack – Multi-object tracking
* OpenCV – Video processing & annotations
* MakeSense.ai – Image annotation tool for YOLO labels

### 📁 Project Structure
![Project Structure](https://drive.google.com/file/d/1eKYLlX4c66ZOnqYz6ZgRWffynvvPxh7t/view?usp=sharing)

### 📊 Data Collection
* Image is collectd from [kaggle](https://www.kaggle.com/datasets/abdullahkhanuet22/eggs-images-classification-damaged-or-not) 
* Some image frames using OpenCV from video
* Frames captured different lighting conditions, angles, and egg densities to improve robustness

### ✍️ Data Annotation

Annotation was performed using [MakeSense.ai](https://makesense.ai)

Annotation Steps:
* Upload extracted image frames
* Create two classes:
    * 0 → Brown Egg
    * 1 → White Egg
* Draw bounding boxes around each egg
* Export annotations in YOLO format
* Split dataset into train and validation

### 🧾 data.yaml Configuration
* path: ../datasets
* train: images/train
* val: images/val
* nc: 2
* names:
  * 0: brown
  * 1: white

### Model Training
YOLO was trained using the annotated dataset:
* yolo detect train \
    * data=datasets/data.yaml \
    * model=yolov8n.pt \
    * epochs=50 \
    * imgsz=640
* After training, the best-performing model was saved as:
    * runs/detect/train/weights/best.pt

### 🎥 Video Inference & Counting Logic
* The trained YOLO model detects eggs frame-by-frame
* ByteTrack assigns a unique ID to each egg
* A vertical counting line is defined
* Eggs are counted only when their center crosses the line
* Each track_id is counted once using a set to prevent duplication

### ▶️ How to Run the Project
* Install Dependencies
    * pip install ultralytics opencv-python
* Run the Tracker
    * python enhanced_egg_count_tracker.py
* Input video
    * Backend/test_video/egg_convoyer_1.mp4
* Output video
    * output_counted.mp4

### Output Features
* Bounding boxes with ID and class label
* Vertical counting line visualization
* Live display of:
    * White egg count
    * Brown egg count
    * Total eggs
* Final summary printed after video ends [final output](https://drive.google.com/file/d/1gisrTER3jqXBbq8SYoqraneAaablA7yJ/view?usp=sharing)


