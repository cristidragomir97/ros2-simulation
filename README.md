This repository provides a base image and overlays docker-based ROS simulations.

## ros2-vnc-base
* Based on Ubuntu Jammy (22.04)
* Full ROS2 Humble installation
* Web remote desktop access trough noVNC at [http://localhost:8080](http://localhost:8080) or trough VNC client on port :5900

To run this image: `docker run -it --rm -p 8080:8080 -p 5900:5900 cristidragomir97/ros2-vnc-base`

## turtlebot 3
* overlay based on ros2-vnc-base for turtlebot3 

To run this image: `docker run -it --rm -p 8080:8080 -p 5900:5900 cristidragomir97/turtlebot3`



