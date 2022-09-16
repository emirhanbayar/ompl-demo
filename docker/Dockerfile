FROM ros:noetic-ros-base

# Set QT_DEBUG_PLUGINS to 1 to inspect errors while running GUI
ENV QT_DEBUG_PLUGINS=1

# Settings to be able to use the GUI  
ENV DISPLAY=$DISPLAY
ENV XAUTHORITY=$XAUTH
VOLUME $XAUTH:$XAUTH

# Install dependencies
RUN apt-get update
RUN apt-get install wget

# Set the workspace where the OMPL will be installed.
WORKDIR $HOME/ws

# Install OMPL
RUN wget https://ompl.kavrakilab.org/install-ompl-ubuntu.sh && \
    chmod u+x install-ompl-ubuntu.sh && \
    ./install-ompl-ubuntu.sh --app

WORKDIR /usr/local/include/

RUN mv ompl-1.5/* ./ && \
    rm -rf ompl-1.5

WORKDIR $HOME/ws
    
