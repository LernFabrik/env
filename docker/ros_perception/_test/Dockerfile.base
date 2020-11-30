ARG ROS_DISTRO
FROM ros:${ROS_DISTRO}-perception

ENV DEBIAN_FRONTEND noninteractive

RUN rm /bin/sh && ln -s /bin/bash /bin/sh
WORKDIR /root

RUN apt-get clean && apt-get update \
    && apt-get -y install build-essential \
    apt-utils \
    wget \
    curl \
    tmux \
    man-db

RUN if [ "$ROS_DISTRO" = "melodic" ]; then \
    echo "Using $ROS_DISTRO" && \
    apt-get install -y python-pip && \
    pip install -U catkin_tools && \
    source /opt/ros/$ROS_DISTRO/setup.bash && \
    mkdir -p /root/catkin_ws/src && \
    cd ~/catkin_ws && \
    catkin init && \
    catkin build && \
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc; \
    else \
    echo "Using $ROS_DISTRO" && \
    apt-get install -y python3-catkin-lint python3-pip && \
    pip3 install -U osrf-pycommon && \
    apt-get install -y python3-catkin-tools && \
    source /opt/ros/$ROS_DISTRO/setup.bash && \
    mkdir -p /root/catkin_ws/src && \
    cd ~/catkin_ws && \
    catkin init && \
    catkin build && \
    echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc; \
    fi