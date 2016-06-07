#Python 2 with Image Processing Libraries
#
# --- Image Stack ---
# chiu0602/python2-imaging
# chiu0602/python2-baseline

FROM chiu0602/python2-baseline

ENV GST_VERSION 0.10

RUN apt-get update && \
  apt-get install -y \
    libgstreamer$GST_VERSION libgstreamer-plugins-base$GST_VERSION \
    libgl1-mesa-dev libglu1-mesa-dev \
    libgtk2.0-dev && \
  apt-get clean autoclean && \
  apt-get autoremove -y
