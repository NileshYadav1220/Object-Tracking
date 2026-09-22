# OpenCV Object Tracking

This is a simple real-time object tracking project made using **Python and OpenCV**.

The program opens the Mac camera, allows the user to select an object from the first frame, and then tracks that object while the camera is running.

I made this project to understand how object tracking works in Computer Vision using OpenCV.

## How it works

1. The program opens the Mac camera.
2. It takes the first frame.
3. We select the object by drawing a rectangle around it.
4. The CSRT tracker is initialized with the selected object.
5. The program reads the camera frames continuously.
6. The tracker finds the object in each frame.
7. A green rectangle is drawn around the object.
8. If the tracker loses the object, it shows `Tracking Failed`.

## Technologies Used

* Python
* OpenCV
* CSRT Tracker
* Mac Camera
* AVFoundation

## Installation

First, install OpenCV:

```bash
pip3 install opencv-contrib-python
```

I used `opencv-contrib-python` because the CSRT tracker is available through the OpenCV legacy tracking module.

## Run the Project

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/opencv-object-tracking.git
```

Go into the project folder:

```bash
cd opencv-object-tracking
```

Run the Python file:

```bash
python3 object_tracking.py
```

## How to use

After running the program, a camera window will open.

Draw a rectangle around the object you want to track.

For example, if I want to track a bottle, I select the bottle using the mouse.

Press:

* `Enter` or `Space` → Select the object
* `C` → Cancel selection
* `Q` → Quit the program

After selecting the object, move it around in front of the camera. The green rectangle should follow the object.

## CSRT Tracker

In this project I used the CSRT tracker:

```python
tracker = cv2.legacy.TrackerCSRT_create()
```

CSRT is one of the object tracking algorithms available in OpenCV.

The tracker is initialized using the first frame and the selected bounding box:

```python
tracker.init(frame, bbox)
```

Then for every new frame:

```python
success, bbox = tracker.update(frame)
```

If the tracker successfully finds the object, the bounding box is updated.

## Project Flow

```text
Camera
   ↓
First Frame
   ↓
Select Object
   ↓
Create Bounding Box
   ↓
Initialize CSRT Tracker
   ↓
Read New Frame
   ↓
Update Tracker
   ↓
Draw Bounding Box
   ↓
Display Video
   ↓
Repeat
```

## Mac Camera

Since I am running this project on macOS, I used the AVFoundation backend:

```python
cv2.VideoCapture(0, cv2.CAP_AVFOUNDATION)
```

If you are using Windows or Linux, you can normally try:

```python
cv2.VideoCapture(0)
```

## If the camera doesn't open

Make sure Python/Terminal has permission to use the camera.

On Mac:

```text
System Settings
→ Privacy & Security
→ Camera
```

Also make sure another application is not already using the camera.

## If CSRT is not available

Install the contrib version of OpenCV:

```bash
pip3 uninstall opencv-python
pip3 install opencv-contrib-python
```

Then check OpenCV:

```bash
python3 -c "import cv2; print(cv2.__version__)"
```

## What I learned from this project

While making this project, I learned about:

* Reading live video using OpenCV
* Working with video frames
* Selecting an ROI (Region of Interest)
* Bounding boxes
* Object tracking
* CSRT tracker
* `cv2.VideoCapture()`
* `cv2.imshow()`
* `cv2.rectangle()`
* Handling keyboard input

## Future Improvements

I can improve this project later by adding:

* Multiple object tracking
* YOLO object detection
* Automatic object detection
* Object counting
* Object movement direction
* Object speed calculation
* Tracking path/history

## Author

**Nilesh Yadav**

