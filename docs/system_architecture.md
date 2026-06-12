                    CRICKET PLAYER

                           │

            ┌──────────────┴──────────────┐

            │                             │

            ▼                             ▼

     Sensor Module                 Video Module

(ESP32 + MPU6050) (Mobile Camera)

            │                             │

            ▼                             ▼

     Sensor Data                 Computer Vision

Acceleration Data OpenCV + MediaPipe

Gyroscope Data Pose Estimation

            │                             │

            └──────────────┬──────────────┘

                           │

                           ▼

                    Feature Fusion

                           │

                           ▼

                  Machine Learning

                           │

          ┌────────────────┼────────────────┐

          ▼                ▼                ▼

Shot Classification Shot Scoring Analytics Engine

          │                │                │

          └────────────────┼────────────────┘

                           │

                           ▼

                    Dashboard

                           │

                           ▼

                Match Strategy Engine

                           │

                           ▼

                     Final Reports



Sensor Data
│
▼
CSV Files
│
▼
PostgreSQL
│
▼
ML Models
│
▼
Dashboard
