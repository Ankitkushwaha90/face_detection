# Face Detection with OpenCV
This project demonstrates real-time face detection using OpenCV and a Haar Cascade classifier. The program captures video from a webcam, processes each frame to detect faces, and displays the result with bounding boxes around detected faces.

## Features
- Real-Time Detection: Utilizes OpenCV's CascadeClassifier for detecting faces in live webcam feed.
- Haar Cascade Classifier: Pre-trained model for frontal face detection.
- Customizable Settings: Adjustable frame dimensions, detection parameters, and escape mechanism.
## Prerequisites
Before running this script, ensure the following are installed:

- Python 3.6+
- OpenCV
- NumPy
Install dependencies using pip:

```bash
pip install opencv-python numpy
```
Setup
Clone the repository:
```bash
git clone https://github.com/yourusername/face-detection-opencv.git
cd face-detection-opencv
```
Ensure the haarcascade_frontalface_default.xml file is in the Cascades directory. If missing, download it from OpenCV GitHub repository.
## How to Run
Save the script as face_detection.py.
Run the script:
```bash
python face_detection.py
```
The webcam feed will open in a window, with detected faces highlighted by rectangles.
Press ESC to exit the program.
# Code Explanation
## 1. Load Haar Cascade Classifier
```python
faceCascade = cv2.CascadeClassifier('Cascades/haarcascade_frontalface_default.xml')
```
Loads the pre-trained Haar Cascade model for frontal face detection.

## 2. Capture Video Stream
```python
cap = cv2.VideoCapture(0)
cap.set(3, 640)  # Set frame width
cap.set(4, 480)  # Set frame height
```
Opens the webcam and sets the frame size.

## 3. Process Each Frame
Convert the frame to grayscale for efficient processing.
Use detectMultiScale to identify faces:
```python
faces = faceCascade.detectMultiScale(
    gray,
    scaleFactor=1.2,
    minNeighbors=5,
    minSize=(20, 20)
)
Parameters:
scaleFactor: Specifies how the image size is reduced at each image scale.
minNeighbors: Specifies how many neighbors each rectangle candidate should have to retain it.
minSize: Minimum object size.
```
## 4. Draw Bounding Boxes
```python
for (x, y, w, h) in faces:
    cv2.rectangle(img, (x, y), (x+w, y+h), (255, 0, 0), 2)
```
Draws rectangles around detected faces.

## 5. Display Output
```python
cv2.imshow('video', img)
```
Opens a window showing the video stream with detected faces.

## 6. Exit Mechanism
```python
k = cv2.waitKey(30) & 0xff
if k == 27:  # Press 'ESC' to quit
    break
```
Allows the user to exit by pressing the ESC key.

### Screenshots
Add screenshots of the face detection window highlighting detected faces.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

### Contributing
Contributions are welcome! Feel free to submit issues and pull requests to improve the project.

This README file provides a clear and comprehensive overview of the project, ensuring ease of use and accessibility for other developers.
