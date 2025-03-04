# Face-Detection-with-Deep-Learning

## Overview
This project implements a face recognition system using deep learning techniques. It detects and identifies faces from a live video stream or a recorded video. The application can recognize known faces, register new faces, and store face metadata for future recognition.

## Features
- **Face Detection**: Detects faces from a video feed using OpenCV and `face_recognition`.
- **Face Recognition**: Identifies known faces by comparing detected faces with a stored dataset.
- **Automatic Face Registration**: Automatically registers new faces and saves metadata such as first seen time, visit count, and last seen time.
- **Live Camera Support**: Supports webcams and Jetson Nano cameras via GStreamer.
- **Persistent Storage**: Stores face encodings and metadata in a file (`known_faces.dat`) to retain information across sessions.

## Requirements
The project requires the following dependencies, which can be installed using:
```bash
pip install -r requirements.txt
```
### Dependencies
- `face_recognition`
- `opencv-python`
- `numpy`

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/ErlendTregde/Face-Detection-with-Deep-Learning.git
   cd Face-Detection-with-Deep-Learning
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the application:
   ```bash
   python doorcam.py
   ```

## How It Works
1. **Loading Known Faces**: If previously stored face encodings exist, they are loaded from `known_faces.dat`.
2. **Face Detection & Recognition**:
   - Captures frames from the webcam.
   - Detects faces and extracts encodings.
   - Compares detected faces with stored encodings.
   - If a match is found, updates the metadata.
   - If no match is found, registers a new face.
3. **Displaying Output**:
   - Draws bounding boxes around detected faces.
   - Displays labels with visit count and time spent at the door.
   - Shows recent visitor thumbnails.
4. **Saving Known Faces**: Periodically saves face encodings and metadata to disk.

## Running on Jetson Nano
If running on a Jetson Nano, the script uses a GStreamer pipeline for camera access.
- The function `get_jetson_gstreamer_source()` constructs a GStreamer pipeline.
- The function `running_on_jetson_nano()` determines if the system is a Jetson Nano and adjusts camera access accordingly.

## File Structure
```
Face-Detection-with-Deep-Learning/
│-- face_recognition/
│-- known_people/
│   │-- erlend.jpg
│   │-- habt.jpg
│   │-- kombo.jpg
│   │-- sander.jpg
│-- unknown_people/
│-- .gitignore
│-- README.md
│-- doorcam.py
│-- known_faces.dat
│-- requirements.txt
```

## Exiting the Application
Press **'q'** to stop the application and save the known faces before exiting.

## Author
- **Erlend Tregde** (Original Contributor)

## License
This project is open-source under the MIT License.

## Notes
- Make sure the webcam is connected and accessible.
- If using a Jetson Nano, install `gstreamer` dependencies for camera support.
- Adjust `face_distance` thresholds in `lookup_known_face()` if needed for better accuracy.

