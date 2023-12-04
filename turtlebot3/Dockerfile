# Source the ROS 2 environment
FROM cristidragomir97/ros2-vnc-base:latest

RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

RUN apt-get install -y wget ros-dev-tools ros-humble-ros-gz
RUN apt-get update && apt-get install -y --no-install-recommends --allow-unauthenticated libgazebo-dev libgazebo11 ros-humble-gazebo-ros-pkgs

RUN mkdir -p /turtlebot3_ws/src
RUN cd /turtlebot3_ws && wget https://raw.githubusercontent.com/ROBOTIS-GIT/turtlebot3/ros2/turtlebot3.repos && . /opt/ros/humble/setup.sh && vcs import src < turtlebot3.repos && colcon build --symlink-install
ENV TURTLEBOT3_MODEL=waffle_pi
ENV GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/turtlebot3_ws/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models

CMD ["/app/entrypoint.sh"]
EXPOSE 8080
EXPOSE 5900

