#Debian with Python, wxpython and omniorb
FROM chiu0602/x11client

USER root

RUN apt-get update && \
  apt-get install -y --no-install-recommends \
    python \
    python-wxgtk3.0 \
    python-omniorb python-omniorb-omg && \
  apt-get clean autoclean && \
  apt-get autoremove -y && \
  cp -r /usr/lib/python2.7/dist-packages/* /usr/local/lib/python2.7/site-packages

#settings for user xclient
USER xclient
ENV HOME /home/xclient
WORKDIR /home/xclient
