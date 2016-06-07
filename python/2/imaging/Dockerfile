#Python 2 with Image Processing Libraries
#
# --- Image Stack ---
# chiu0602/python2-imaging
# chiu0602/python2-baseline

FROM chiu0602/python2-baseline

RUN apt-get update && \
  apt-get install -y \
    libgstreamer0.10-dev \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-ugly \
    gstreamer1.0-pulseaudio \
    gstreamer1.0-plugins-bad \
    libgl1-mesa-dev libglu1-mesa-dev \
    libgtk2.0-dev && \
  apt-get clean autoclean && \
  apt-get autoremove -y
