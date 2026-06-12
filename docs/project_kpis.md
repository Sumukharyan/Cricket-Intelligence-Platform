# Cricket Intelligence Platform

# Key Performance Indicators (KPIs)

---

# Project Goal

The objective of this project is to analyze cricket batting performance using:

- Sensor Analytics
- Computer Vision
- Machine Learning
- Sports Analytics

The system will generate performance metrics for players, coaches, and analysts.

---

# SECTION 1

# Player Analytics KPIs

These KPIs evaluate the technical quality of a batsman's shot.

---

## 1. Bat Speed

### Definition

Measures the speed of the bat during the downswing.

### Source

- MPU6050 Gyroscope
- Accelerometer

### Why Important

Higher bat speed generally leads to:

- Greater power
- Better boundary percentage

### Target Output

Bat Speed (km/h)

Example:

Bat Speed = 92 km/h

---

## 2. Swing Duration

### Definition

Time taken from backswing to impact.

### Source

Sensor Data

### Why Important

Indicates shot efficiency.

A shorter and controlled swing often reflects better technique.

### Output

Swing Duration (milliseconds)

---

## 3. Swing Angle

### Definition

Angle of the bat during the shot.

### Source

Gyroscope

### Why Important

Different shots require different swing paths.

Useful for shot classification.

### Output

Degrees

---

## 4. Head Stability Score

### Definition

Measures head movement during execution.

### Source

MediaPipe Pose Estimation

### Why Important

Elite batsmen maintain a stable head position.

Improves:

- Timing
- Shot control

### Output

0-100

---

## 5. Balance Score

### Definition

Measures body stability throughout the shot.

### Source

Pose Estimation

### Why Important

Good balance improves consistency.

### Output

0-100

---

## 6. Follow Through Score

### Definition

Measures completion of bat swing after impact.

### Source

Computer Vision

### Why Important

Proper follow through indicates efficient energy transfer.

### Output

0-100

---

# SECTION 2

# Performance Analytics KPIs

---

## 7. Timing Score

### Definition

Measures quality of ball-bat contact.

### Why Important

Timing is one of the most important batting metrics.

### Output

0-100

---

## 8. Power Score

### Definition

Measures force generation during the shot.

### Inputs

- Bat Speed
- Acceleration

### Output

0-100

---

## 9. Stability Score

### Definition

Measures body control during shot execution.

### Inputs

- Head Stability
- Balance

### Output

0-100

---

## 10. Shot Quality Score

### Definition

Overall batting performance metric.

### Inputs

- Timing
- Power
- Stability
- Follow Through

### Output

0-100

Example:

Shot Quality = 89

---

# SECTION 3

# Shot Classification KPIs

---

## 11. Shot Type

### Categories

- Cover Drive
- Straight Drive
- Pull Shot
- Cut Shot
- Sweep Shot

### Source

Machine Learning Model

---

## 12. Shot Classification Accuracy

### Definition

Accuracy of shot prediction model.

### Target

85%+

---

# SECTION 4

# Match Strategy KPIs

---

## 13. Win Probability

### Definition

Predicted probability of winning the match.

### Inputs

- Score
- Wickets
- Overs
- Target

### Output

0-100%

---

## 14. Expected Score

### Definition

Predicted final innings score.

### Output

Runs

Example:

Expected Score = 184

---

## 15. Bowler Recommendation

### Definition

Suggests the best bowler for the current situation.

### Inputs

- Batter History
- Match Situation
- Venue Data

### Output

Recommended Bowler

---

## 16. Matchup Score

### Definition

Measures performance of a batsman against a bowler.

### Output

0-100

---

# SECTION 5

# Dashboard KPIs

The final dashboard should display:

- Bat Speed
- Swing Angle
- Timing Score
- Power Score
- Stability Score
- Shot Quality Score
- Shot Distribution
- Win Probability
- Expected Score
- Bowler Recommendation

---

# Success Criteria

The project will be considered successful if:

- Shot Classification Accuracy > 85%
- Dashboard Operational
- Sensor Data Collection Successful
- Computer Vision Pipeline Operational
- Match Strategy Engine Functional
