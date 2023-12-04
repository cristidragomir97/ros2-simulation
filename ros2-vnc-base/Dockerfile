# Start from the ROS Humble full desktop image
FROM ubuntu:22.04


# Set the noninteractive frontend (useful for Docker builds)
ENV DEBIAN_FRONTEND=noninteractive

# Update the package repository
RUN apt-get update && apt-get upgrade -y

# Install necessary tools
RUN apt-get install -y curl gnupg2 lsb-release 

# Add the ROS 2 repository
RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Update the package repository
RUN apt-get update && apt-get install -y --no-install-recommends --allow-unauthenticated ros-humble-desktop ros-humble-rosbag2

# Source the ROS 2 environment
RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

RUN set -ex; \
    apt-get update; \
    apt-get install -y \
      bash \
      lxde  \
      git \
      net-tools \
      novnc \
      gtk2-engines-murrine \
      supervisor \
      x11vnc \
      xterm \
      xvfb

ENV HOME=/root \
    DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=C.UTF-8 \
    DISPLAY=:0.0 \
    DISPLAY_WIDTH=1920 \
    DISPLAY_HEIGHT=1080 

COPY . /app
RUN chmod +x /app/entrypoint.sh
CMD ["/app/entrypoint.sh"]
EXPOSE 8080
EXPOSE 5900
