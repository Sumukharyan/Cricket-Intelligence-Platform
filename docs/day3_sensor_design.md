# Sensor Architecture

Hardware Components:

1. ESP32
2. MPU6050
3. Power Bank/Battery
4. Cricket Bat

The MPU6050 will be mounted near the handle of the bat.
Handle Placement near the handle:

- Safer
- Better rotational data

The ESP32 collects sensor readings and sends them to a laptop through USB or WiFi.

The collected data is stored as CSV files for analysis.

Cricket Bat

     │

     ▼

MPU6050 Sensor

     │

     ▼

    ESP32

     │

     ▼

Laptop / CSV File

     │

     ▼

Analytics Engine

| Sensor        | Axis | Purpose                 |
| ------------- | ---- | ----------------------- |
| Accelerometer | X    | Forward/Backward Motion |
| Accelerometer | Y    | Side Motion             |
| Accelerometer | Z    | Vertical Motion         |
| Gyroscope     | X    | Rotation Around X       |
| Gyroscope     | Y    | Rotation Around Y       |
| Gyroscope     | Z    | Rotation Around Z       |

| Sensor Reading    | KPI Generated       |
| ----------------- | ------------------- |
| Angular Velocity  | Bat Speed           |
| Peak Acceleration | Power Score         |
| Swing Duration    | Swing Efficiency    |
| Rotation Pattern  | Shot Classification |

# Video Collection Protocol

The objective of video collection is to capture batting movements in a consistent format for pose estimation and cricket shot analysis.

The collected videos will be used for:

- Pose Estimation
- Head Stability Analysis
- Shoulder Rotation Analysis
- Hip Rotation Analysis
- Follow Through Analysis
- Shot Classification

## Final Dataset Target

250 Videos

50 Cover Drives
50 Straight Drives
50 Pull Shots
50 Cut Shots
50 Sweep Shots

All videos will be recorded using a side-view camera setup at 1080p resolution and 60 FPS where possible.

# Shot Labeling Strategy

| Class ID | Shot Type      |
| -------- | -------------- |
| 0        | Cover Drive    |
| 1        | Straight Drive |
| 2        | Pull Shot      |
| 3        | Cut Shot       |
| 4        | Sweep Shot     |

### labels.csv

The labels.csv file stores the ground-truth class labels used for supervised machine learning.

Each shot is assigned:

- shot_id
- shot_type
- class_id

This file enables machine learning models to learn the relationship between batting features and shot categories.

### dataset_master.csv

The dataset_master.csv file acts as the central index of the project.

It links:

- Video files
- Sensor files
- Shot labels

using a unique shot_id.

# Feature Engineering Blueprint

Our project has two sources of data:

1. Sensor Data (MPU6050)
2. Vision Data (MediaPipe)

## Sensor Features

| Feature               | Source                    | Why Important             |
| --------------------- | ------------------------- | ------------------------- |
| Peak Acceleration     | Accelerometer             | Measures power generation |
| Mean Acceleration     | Accelerometer             | Measures swing smoothness |
| Peak Angular Velocity | Gyroscope                 | Estimates bat speed       |
| Mean Angular Velocity | Gyroscope                 | Swing consistency         |
| Swing Duration        | Accelerometer + Gyroscope | Measures shot efficiency  |
| Swing Angle           | Gyroscope                 | Helps identify shot type  |

## Vision Features

| Feature               | Source    | Why Important                   |
| --------------------- | --------- | ------------------------------- |
| Head Stability        | MediaPipe | Measures timing quality         |
| Shoulder Rotation     | MediaPipe | Indicates power generation      |
| Hip Rotation          | MediaPipe | Measures footwork effectiveness |
| Body Balance          | MediaPipe | Measures stability              |
| Follow Through Length | MediaPipe | Measures technique quality      |
| Elbow Angle           | MediaPipe | Helps distinguish shot types    |

## Analytics Features

These are features created from sensor + vision data.

| Analytics Feature    | Derived From                   |
| -------------------- | ------------------------------ |
| Timing Score         | Head Stability + Impact Timing |
| Power Score          | Bat Speed + Acceleration       |
| Balance Score        | Body Alignment                 |
| Follow Through Score | Swing Completion               |
| Shot Quality Score   | Combined Metrics               |

## Final Pipeline Diagram

MPU6050 Data
│
▼

Sensor Features
│

MediaPipe Data
│
▼

Vision Features
│

Feature Fusion
│
▼

Feature Vector
│
▼

Machine Learning Model
│
▼

Shot Classification
│
▼

Analytics Scores

The Feature Engineering Blueprint defines how raw sensor and vision data are transformed into machine learning features.

A total of ten primary features will be extracted from MPU6050 sensor readings and MediaPipe pose landmarks. These features form the input to the shot classification model and analytics engine.
