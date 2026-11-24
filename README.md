# Smart India Hackathon Workshop
# Date: 24/11/2026
## Reference Number: 26001563
## Name: B Kevin Larsen

## Problem Title
SIH 26033: Autonomous Drone and Thermal Vision System for Post-Earthquake Search and Rescue

## Problem Creater's Organization
National Disaster Management Authority (NDMA) / Ministry of Home Affairs

## Theme
Disaster Management & Robotics / Drones

## Problem Description


Benefits:

Rapid scanning of large disaster zones, drastically reducing search times.

Enhanced safety for rescue teams by minimizing entry into unstable structures.

Higher survivor detection accuracy in zero-visibility or obstructed conditions..

## Proposed Solution
1. Detailed Explanation of the Proposed SolutionWe propose AeroSense-SAR, an autonomous quadcopter system integrated with a dual-spectrum camera payload (LWIR Thermal + RGB) and onboard edge-AI processing. When deployed over an earthquake-affected zone, the drone executes automated grid-search patterns or navigates through partially collapsed structures using LiDAR-based SLAM (Simultaneous Localization and Mapping). Onboard neural networks analyze thermal frames in real time to isolate human heat signatures ($36^\circ\text{C} - 37.5^\circ\text{C}$) from ambient rubble heat, marking potential survivor locations on a live 3D situational map for first responders.
   2. How It Addresses the ProblemSpeed & Coverage: Covers up to $10\times$ more area per hour than ground teams on foot.All-Condition Visibility: Long-Wave Infrared (LWIR) sensors penetrate dense dust, smoke, and total darkness where standard optical cameras fail.GPS-Denied Navigation: Visual-Inertial Odometry (VIO) and 3D LiDAR allow the drone to navigate indoor/semi-collapsed spaces without relying on satellite signals.
   3. Innovation and Uniqueness of the SolutionMulti-Modal Sensor Fusion: Combines thermal anomaly detection with RGB visual verification and directional acoustic sensors (to detect faint tapping or vocal cries) to eliminate false positives from fires or warm machinery.Edge-AI Execution: Runs lightweight, quantized object-detection models directly on the drone’s companion computer, eliminating reliance on high-bandwidth cellular networks that are often destroyed during earthquakes.Swarm Scalability: Designed with a decentralized mesh communication protocol allowing multiple drones to divide search zones dynamically without overlapping.

## Technical Approach
1. Technologies to be UsedHardware: Custom Carbon-Fiber Quadcopter Frame, Pixhawk 6C Flight Controller, NVIDIA Jetson Orin Nano (Edge AI), FLIR Boson / Lepton 3.5 Thermal Camera, Intel RealSense Depth Camera / 2D-3D LiDAR, LoRa / Mesh Telemetry Module.Software & Frameworks: ROS 2 (Robot Operating System), PX4 Autopilot, Python, C++, OpenCV, PyTorch / TensorRT (YOLOv8-Thermal), MAVLink.Ground Control Station (GCS): QGroundControl integrated with a custom React/Leaflet real-time dashboard for triage mapping.
   2. Methodology and Process for ImplementationDeployment & Area Mapping: Rescue operators define a geofenced polygon on the GCS dashboard.Autonomous Path Planning: The system generates an optimal coverage path (Lawnmower/Spiral pattern) while activating real-time obstacle avoidance via LiDAR/Depth sensors.Edge Inference & Detection: Thermal and RGB frames are fused and processed at $30\text{ FPS}$ on the Jetson Orin Nano. If a human thermal profile is detected with $>85\%$ confidence, the drone hovers to capture multi-angle verification.Alert & Triage Transmission: Encrypted low-bandwidth packets containing exact coordinates, thermal snapshots, and confidence scores are transmitted via mesh radio to the rescue team's mobile interface.
      
## Feasibility and Viability
1. Analysis of the Feasibility of the IdeaTechnical Feasibility: Off-the-shelf flight controllers (PX4), compact edge-AI modules (Jetson), and commercial LWIR sensors make prototyping and scaling highly achievable within current hardware ecosystems.Operational Feasibility: Requires minimal operator training due to one-click autonomous mission execution and intuitive visual alerts.
   2. Potential Challenges and RisksThermal False Positives: Sun-heated concrete, fires, or trapped animals may mimic human heat signatures.Battery Endurance: Carrying heavy payloads (LiDAR + Thermal + Compute) reduces flight time to $20\text{--}25\text{ minutes}$.Communication Blackouts: Destroyed cellular towers can sever standard telemetry links.
      3. Strategies for Overcoming These ChallengesAdaptive Thermal Calibration: Dynamically adjusts temperature thresholds based on ambient environment readings and cross-verifies targets using skeletal/pose estimation and micro-motion detection (breathing/movement).Hot-Swappable Battery Bays & Relay Drones: Standardized quick-release batteries minimize downtime, while a high-altitude tether/relay drone extends communication range via LoRa mesh networking.

## Impact and Benefits
1. Potential Impact on the Target Audience

Disaster Response Forces (NDRF/SDRF): Empowers rescue teams with actionable, pinpointed survivor coordinates within minutes of arrival, optimizing manpower allocation.

Earthquake Victims: Dramatically increases survival rates by locating trapped individuals well within the critical 72-hour window.

2. Benefits of the Solution

Social Impact: Saves human lives and reduces casualties among first responders entering hazardous zones.

Economic Impact: Lowers the cost of large-scale search operations compared to manned helicopter deployments and accelerates disaster recovery timelines.

Environmental & Operational Safety: Zero-emission electric propulsion with low acoustic footprint, allowing sensitive acoustic sensors to pick up faint survivor distress signals.

## Research and References
1. FLIR Thermal Datasets for Search & Rescue: Teledyne FLIR Free ADAS Thermal Dataset

2. PX4 & ROS 2 Autonomous Navigation: PX4 Autopilot Official Documentation

3. Deep Learning for Thermal Human Detection: Kieu, M., et al. "Task-conditioned Domain Adaptation for Pedestrian Detection in Thermal Imagery" (ECCV).

4. NDMA Guidelines on Earthquake Management: National Disaster Management Authority, Govt. of India
