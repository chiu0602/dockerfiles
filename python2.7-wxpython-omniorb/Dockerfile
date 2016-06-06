#Python 2.7 with wxpython and omniorb
FROM luzh/python2.7-wxpython

ENV OMNIORB_VERSION 4.2.1

RUN \
  curl -SL "https://sourceforge.net/projects/omniorb/files/omniORB/omniORB-$OMNIORB_VERSION/omniORB-$OMNIORB_VERSION-2.tar.bz2" -o omniORB.tar.bz2 && \
  mkdir -p /build/omniORB && \
  tar -jxvf omniORB.tar.bz2 --strip-components=1 -C /build/omniORB && \
  cd /build/omniORB && \
  ./configure && \
  ./config.status && \
  make && \
  make install && \
  curl -SL "https://sourceforge.net/projects/omniorb/files/omniORBpy/omniORBpy-$OMNIORB_VERSION/omniORBpy-$OMNIORB_VERSION-2.tar.bz2" -o omniORBpy.tar.bz2 && \
  mkdir /build/omniORBpy && \
  tar -jxvf omniORBpy.tar.bz2 --strip-components=1 -C /build/omniORBpy && \
  cd /build/omniORBpy && \
  ./configure --with-omniorb=/build/omniORB && \
  ./config.status && \
  make && \
  make install
  
