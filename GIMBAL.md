# Vision-Guided Pan/Tilt Tracking System
> A real-time closed-loop vision and control system for autonomous target tracking and gimbal stabilization

### Quick Specs
- Control Loop: ~25–30 Hz
- Latency: <30 ms frame-to-servo
- Accuracy: ±2° steady-state
- States: TRACK / LOST
- Sensors: CSI camera (ArUco)
- Actuation: Dual-axis servo gimbal

## 1. System Overview
This project is a closed-loop vision tracking system designed to autonomously center a moving target using a Raspberry Pi, camera module, and servo-driven pan/tilt mechanism. The system integrates real-time perception, control, and actuation in a unified feedback loop, maintaining stable tracking performance under variable lighting, target motion, and mechanical disturbances.

The platform is designed as a modular testbed for multi-sensor control systems, enabling future expansion into inertial stabilization, multi-target tracking, and sensor fusion architectures commonly used in robotics, aerospace, and autonomous surveillance systems.

---

## 2. System Requirements
- Track a moving target within **±2° steady-state angular error**  
- End-to-end latency below **30 ms** from frame capture to servo command output  
- Maintain reliable tracking at distances up to **3 meters**  
- Recover from target loss within **15 seconds** through autonomous reacquisition behavior  
- Prevent mechanical overtravel through **software-enforced angular limits**  
- Support real-time telemetry logging for post-run performance analysis  

---

## 3. System Architecture

**Camera → Image Processing → Target Detection → Control Algorithm → Servo Actuation → Visual Feedback Loop**

The system operates as a deterministic feedback loop in which image-space error is continuously converted into angular servo commands. A browser-based monitoring interface provides real-time visualization of tracking state, target error, servo angles, and system frame rate, enabling live tuning and validation.

---

## 4. Hardware Design

### Core Components
- **Compute Platform:** Raspberry Pi 5  
- **Camera Module:** Arducam IMX708 (wide-angle CSI interface camera)  
- **Actuators:** 2× MG996R high-torque servo motors (pan and tilt axes)  
- **Servo Controller:** PCA9685 16-channel PWM driver (I²C)  
- **Mounting System:** 2-DOF pan/tilt gimbal with software-defined mechanical limits  
- **Power System:** External 6 V rail with ≥5 A peak current capability for servo load isolation  

### Electrical Interface
- **I²C:** Raspberry Pi ↔ PCA9685  
- **CSI:** Raspberry Pi ↔ Camera Module  
- **PWM:** PCA9685 ↔ Servo Motors  
- **Grounding:** Common-ground architecture across logic and power domains  

---

## 5. Software & Control Logic

### Runtime Environment
- **Operating System:** Raspberry Pi OS (Linux)  
- **Primary Language:** Python  

### Perception
- **Image Processing:** OpenCV  
  - Grayscale conversion  
  - Fiducial detection pipeline  
- **Target Detection:** ArUco marker tracking with dictionary-based ID filtering  

### Control Strategy
**Rate-limited proportional closed-loop controller with deadband stabilization**

- Image-space pixel error is mapped to angular servo commands  
- Deadband suppresses micro-oscillations near the target center  
- Angular rate limiting prevents overshoot and mechanical stress  
- Finite-state logic governs system behavior:
  - `TRACK` — Active closed-loop target following  
  - `LOST` — Target absence detection and hold/reacquisition behavior  

### Communication & Interfaces
- **Servo Control:** I²C → PCA9685 → PWM  
- **Live Telemetry:** Flask-based MJPEG server (browser visualization)  
- **Logging:** CSV telemetry output for offline analysis  

### Performance
- **Vision Processing Rate:** ~25–30 Hz  
- **Streaming Rate:** 10–15 FPS (throttled, non-blocking)  
- **Control Loop:** Fixed-rate execution with bounded angular step size  

---

## 6. Test & Validation

### Metrics Measured
- **Tracking Error:** Angular deviation (degrees vs. time)  
- **System Latency:** Frame timestamp to servo command output  
- **Recovery Time:** Time to reacquire target after loss  
- **Stability:** Oscillation amplitude near steady-state center  

### Test Setup
- Camera mounted to pan/tilt gimbal at the rotational axes to maintain closed-loop visual feedback  
- Target implemented using a high-contrast ArUco fiducial marker (8–12 cm width)  
- Controlled indoor lighting with variable ambient illumination to test robustness  
- Target motion introduced manually across horizontal and vertical axes at varying speeds  
- Telemetry captured via CSV logging, including timestamped pixel error, servo angles, and tracking state  

### Results
- Stable closed-loop tracking achieved at typical indoor distances up to ~3 m  
- Deadband and rate limiting significantly reduced servo oscillation near target center  
- System successfully transitioned between `TRACK` and `LOST` states under occlusion and re-entry scenarios  
- Live browser telemetry enabled rapid tuning of controller gains and mechanical limits  

---

## 7. Failure Modes & Iterations

### Observed Failure Modes
- **Target Loss Under Glare:** Specular reflections from screen-based markers reduced detection reliability  
- **Mechanical Overtravel:** Initial configuration allowed gimbal collision at angular extremes  
- **Power Brownout:** Insufficient servo power supply caused transient resets and I²C communication faults  
- **Detection Dropouts at Low Resolution:** Reduced camera resolution degraded fiducial detection reliability  

### Design Iterations
- Introduced software-defined **soft limits** on pan/tilt angles  
- Isolated servo power domain using an external high-current 6 V rail  
- Added deadband and angular rate limiting to stabilize control response  
- Increased camera resolution for detection reliability while throttling stream encoding to preserve performance  

---

## 8. Next Improvements
- **IMU Integration:** Add inertial sensing for horizon stabilization and multi-sensor fusion control modes  
- **SEARCH State:** Implement autonomous pan/tilt sweep for intelligent target reacquisition  
- **Non-Fiducial Tracking:** Replace ArUco detection with neural network-based object detection  
- **PID Control:** Extend proportional controller to full PID for improved transient response  
- **System Identification:** Characterize servo dynamics for model-based control tuning  
- **Web Dashboard:** Replace MJPEG stream with WebRTC-based low-latency visualization and control interface  

---

## 9. Demo & Artifacts
- **Live Browser View:** Real-time MJPEG stream with overlayed telemetry (state, FPS, servo angles, pixel error)  
- **Telemetry Logs:** CSV output for post-run analysis and performance characterization  
- **Video Demo:** Short-form recording demonstrating closed-loop tracking and recovery behavior  

---

## 10. Tech Stack
- Python  
- OpenCV  
- Flask  
- Raspberry Pi OS  
- I²C / PWM / CSI  
- PCA9685 Servo Driver  
- ArUco Fiducial Tracking  
