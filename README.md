This code simulates a complete Vessel Tracking Pipeline, moving from data preparation to a tracking simulation using sensor fusion.

Here is a short breakdown of its four main functions:

1. Data Preparation (YOLO Labeling) It defines a function to automatically generate YOLO-format annotation files (.txt) for all 5,600 training images. It assigns class IDs (e.g., 0 for Ore Carrier) and mock bounding boxes, preparing the dataset for object detection training.

2. Ground Truth Generation It uses real AIS data (speed and course over ground) to mathematically calculate a "perfect" ship trajectory (Ground Truth) over 1,400 frames using Dead Reckoning formulas. This serves as the reference path the ship actually took.

3. Kalman Filter Simulation (Sensor Fusion)

This is the core tracking logic. It simulates a noisy sensor (like a camera) by adding random errors to the Ground Truth coordinates. It then uses a Kalman Filter to:

Predict the ship's next position based on physics.

Update that prediction using the noisy measurement.

Result: A smooth, estimated path that filters out the sensor noise.

4. Evaluation It calculates the RMSE (Root Mean Square Error) to quantify how accurate the tracking is in meters. Finally, it generates a plot comparing the True Path vs. Noisy Measurements vs. Kalman Filter Estimate to visually prove the filter works.
