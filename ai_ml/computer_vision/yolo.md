# YOLO

## What YOLO Is (In AI)

### YOLO — "You Only Look Once"

**YOLO (You Only Look Once)** is a **real-time object detection model** used in **computer vision**.

It detects **multiple objects in an image at once** and draws bounding boxes around them.

Example detections:

```
Person
Car
Dog
Bicycle
Traffic light
```

### How YOLO Works (Simple)

Traditional detection systems:
```
Step 1: Find possible objects
Step 2: Classify each object
```

YOLO does it in one **pass through the neural network**.
```
Image → Neural Network → Objects + Bounding Boxes
```

Internally it:

1. Splits image into grid cells

2. Each grid predicts:

    - bounding box

    - confidence score

    - class label

Example output:
```
Object: Dog
Confidence: 0.91
Location: (x, y, width, height)
```

### Why YOLO Is Popular

Advantages:

⚡ Real-time detection

🎯 High accuracy

🧠 Single neural network

🚗 Used in self-driving cars

📷 Used in surveillance

🤖 Used in robotics