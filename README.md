# NumPy to PointCloud2 (ROS2)

## Overview
This project was part of a larger goal for the LIDAR team in Triton AI to implement k-means visualization and bounding boxes.

My task was to convert 3D data points stored in NumPy arrays in the form of [x-coordinate, y-coordinate, z-coordinate, cluster number] into ROS2 PointCloud2 messages for visualization in RViz2, where each visualized point would be colored according to their cluster number.

At the same time, I was learning how ROS2 nodes communicate through publishers and subscribers.

Initial implementation was generated with AI assistance but was later modified to become compatable with other nodes coded for the larger goal and to better understand ROS2 nodes.

## Tech Used
- Python
- Foxy ROS2
- NumPy
- RViz2
- MobaXTerm
- 20.04 Ubuntu

## Features
- `setup.py`: ROS2 package configuration
- `numpy-to-pointcloud2-ros2`: main script that subscribes to a NumPy array, converts each 3D data point in the NumPy array into a PointCloud2 message, and publishes all of the PointCloud2 messages to a topic for RViz2 to subscribe to
- `numpy_points_generator.py`: a test script that publishes 300 3D data points with the format [x-coordinate, y-coordinate, z-coordinate, cluster number] in a NumPy array

## Visualization of Results
<img width="1919" height="1132" alt="Screenshot 2026-03-29 162814" src="https://github.com/user-attachments/assets/cfd8eca6-327f-4990-9e8b-634d175a62a9" />

## What I learned
- How ROS2 nodes, publishers, and subscribers work together
- Setting up and running Foxy ROS2 in 20.04 Ubuntu environment
- Visualizing PointCloud2 messages in RViz2
