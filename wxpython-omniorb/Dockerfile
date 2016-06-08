#Debian with Python, wxpython and omniorb
FROM chiu0602/x11client

USER root

#wxpython dependencies
ENV GST_VERSION 0.10
RUN apt-get update && \
  apt-get install -y \
    python python-dev \
    libgstreamer$GST_VERSION libgstreamer-plugins-base$GST_VERSION \
    libgl1-mesa-dev libglu1-mesa-dev \
    libgtk2.0-dev && \
  apt-get clean autoclean && \
  apt-get autoremove -y

#install wxpython
ENV WXPYTHON_VERSION 3.0.2.0

RUN mkdir /build && \
  cd /build && \
  curl -SL "http://sourceforge.net/projects/wxpython/files/wxPython/$WXPYTHON_VERSION/wxPython-src-$WXPYTHON_VERSION.tar.bz2" -o wxPython.tar.bz2 && \
  mkdir /build/wxPython && \
  tar -jxvf wxPython.tar.bz2 --strip-components=1 -C /build/wxPython && \
  cd /build/wxPython/wxPython && \
  python ./build-wxpython.py --build_dir=../wxBuild && \
  python ./build-wxpython.py --install --build_dir=../wxBuild && \
  cd && rm -rf /build && \
  ldconfig

#install omniorb
RUN apt-get update && \
  apt-get install -y \
  omniidl \
  omniidl-python \
  omniorb-nameserver \
  python-omniorb \
  python-omniorb-doc && \
  apt-get clean autoclean && \
  apt-get autoremove -y && \
  cp -r /usr/lib/python2.7/dist-packages/* /usr/local/lib/python2.7/site-packages

#settings for user xclient
USER xclient
ENV HOME /home/xclient
WORKDIR /home/xclient