🥚 Egg Counting & Classification System using YOLO + ByteTrack
📌 Project Overview

This project implements an automated egg detection, classification, tracking, and counting system from conveyor belt videos using Computer Vision and Deep Learning.
Eggs are detected and classified as White (cls=1) or Brown (cls=0), tracked with unique IDs, and counted only when they cross a vertical counting line to prevent duplicate counts.

🎯 Objectives

Detect eggs in real-time from video streams

Classify eggs into White and Brown

Track each egg across frames using ByteTrack

Count eggs accurately when crossing a defined border line

Generate annotated videos showing egg detection and counts

🧠 Tech Stack

Python 3.12+

YOLOv8 (Ultralytics) – Object Detection

ByteTrack – Multi-object tracking

OpenCV – Video processing & annotations

MakeSense.ai – Image annotation tool for YOLO labels
