FROM ros:noetic-ros-base

ENV QT_QPA_PLATFORM=offscreen
ENV QT_DEBUG_PLUGINS=1

ENV DISPLAY=$DISPLAY
ENV XAUTHORITY=$XAUTH

VOLUME $XAUTH:$XAUTH

ENV ROS_UNDERLAY /ws/devel
ENV CATKIN_WS $(realpath $ROS_UNDERLAY/..)

# Install dependencies
RUN apt-get update
RUN apt-get install wget
    
RUN apt-get install -y xserver-xorg-video-all
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libgl1-mesa-dri \
    && rm -rf /var/lib/apt/lists/*
RUN usermod -a -G video <username>

WORKDIR $ROS_UNDERLAY/..

# Install OMPL and dependencies
RUN wget https://ompl.kavrakilab.org/install-ompl-ubuntu.sh && \
    chmod u+x install-ompl-ubuntu.sh && \
    ./install-ompl-ubuntu.sh --app
    
