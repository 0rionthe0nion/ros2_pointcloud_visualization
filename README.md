# NumPy to PointCloud2 (ROS2)

## Overview
This project was part of a larger goal for the LIDAR team in Triton AI to implement k-means visualization and bounding boxes.

My task was to convert 3D data points stored in NumPy arrays in the form of [x-coordinate, y-coordinate, z-coordinate, cluster number] into ROS2 PointCloud2 messages for visualization in RViz2, where each visualized point would be colored according to their cluster number.

At the same time, I was learning how ROS2 nodes communicate through publishers and subscribers.

Initial implementation was generated with AI assistance but was later modified to become compatable with other nodes coded for the larger goal and to better understand ROS2 nodes.

## Running the Project
This project requires that Foxy ROS2 be installed on 20.04 Ubuntu. If you do not have Foxy ROS2 installed, please follow the official download instructions here: [https://docs.ros.org/en/foxy/Installation/Alternatives/Ubuntu-Development-Setup.html](url)

Download all files and move them into your FOXY ROS2 workspace folder. If you followed the instructions from the link above, move the project into `/ros2_ws/src/`.

- To run the main program `numpy_to_pointcloud2_ros2.py`, make sure you have a NumPy array with 3D data points in the form of [x-coordinate, y-coordinate, z-coordinate, cluster number] being published to a topic called `points_array`. Then, run these commands in Ubuntu 20.04:

`source /opt/ros/foxy/setup.bash`

`cd ~/ros2_ws `

`colcon build`

`source install/setup.bash`

`ros2 run my_pkg turn_points_to_pc2`

- To run the test program `numpy_points_generator.py`, run these commands in Ubuntu 20.04:

`source /opt/ros/foxy/setup.bash`

`cd ~/ros2_ws`

`colcon build`

`source install/setup.bash`

`ros2 run my_pkg print_points_with_k_value`

- Running RViz2 proved to be challenging for me; these commands are what I used to get RViz2 working:

`unset LIBGL_ALWAYS_INDIRECT`

`export LIBGL_ALWAYS_SOFTWARE=1`

`export MESA_GL_VERSION_OVERRIDE=3.3`

`export OGRE_RTT_MODE=Copy`

`source /opt/ros/foxy/setup.bash`

`rviz2`

Add a PointCloud2 display, subscribe to topic `point_cloud` for point visualization, and set channel name to `k` to display clusters.


## Tech Used
- Python
- Foxy ROS2
- NumPy
- RViz2
- MobaXTerm
- 20.04 Ubuntu

## Features
- `setup.py`: ROS2 package configuration
- `numpy_to_pointcloud2_ros2.py`: main script that subscribes to a NumPy array, converts each 3D data point in the NumPy array into a PointCloud2 message, and publishes all of the PointCloud2 messages to a topic for RViz2 to subscribe to
- `numpy_points_generator.py`: a test script that publishes 300 3D data points with the format [x-coordinate, y-coordinate, z-coordinate, cluster number] in a NumPy array

## Visualization of Results
<img width="1919" height="1132" alt="Screenshot 2026-03-29 162814" src="https://github.com/user-attachments/assets/cfd8eca6-327f-4990-9e8b-634d175a62a9" />

## What I learned
- How ROS2 nodes, publishers, and subscribers work together
- Setting up Foxy ROS2 in 20.04 Ubuntu environment
- Running nodes in 20.04 Ubuntu environment
- Visualizing PointCloud2 messages in RViz2
