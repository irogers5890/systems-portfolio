# Vision-Guided Pan/Tilt Tracking System

## 1. System Overview
This project is a closed-loop vision tracking system designed to autonomously center a moving target using a Raspberry Pi, camera module, and servo-driven pan/tilt mechanism. The system integrates perception, control, and actuation while maintaining stable performance under variable lighting and motion conditions.

## 2. System Requirements
- Track a moving target within ±2° steady-state error  
- End-to-end latency below 30 ms from frame capture to servo response  
- Maintain tracking at distances up to 3 meters  
- Recover from target loss within 15 seconds  

## 3. System Architecture
Camera → Image Processing → Target Detection → Control Algorithm → Servo Actuation → Visual Feedback Loop

## 4. Hardware Design
- Raspberry Pi: 5  
- Camera Module: Arducam IMX708  
- Servo Motors: 2 MG996R  
- Mounting System: In progress.
- Power System: 6 V supply with 5 A peak draw  

## 5. Software & Control Logic
- Image Processing: OpenCV   
- Control Strategy: ___ (PID / proportional / heuristic tracking)  
- Frame Rate: 30 FPS  
- Communication: PWM/I2C/GPIO

## 6. Test & Validation
### Metrics Measured
- Tracking error (degrees vs. time)  
- Latency (frame timestamp to servo movement)  
- Recovery time after target loss  

### Test Setup
Describe camera placement, lighting conditions, moving target method, and how measurements were captured.

### Results
In progress. 

## 7. Failure Modes & Iterations
In progress.

## 8. Next Improvements

