#Python 2 with wxpython and omniorb
#
# --- Image Stack ---
# chiu0602/python2-wxpython-omniorb
# chiu0602/python2-imaging
# chiu0602/python2-baseline

FROM chiu0602/python2-imaging

ENV WXPYTHON_VERSION 3.0.2.0

RUN apt-get update && \
  apt-get install -y \
  omniidl \
  omniidl-python \
  omniorb-nameserver \
  python-omniorb \
  python-omniorb-doc && \
  rm -rf /var/lib/apt/lists/*

RUN mkdir /build && \
  cd /build && \
  curl -SL "http://sourceforge.net/projects/wxpython/files/wxPython/$WXPYTHON_VERSION/wxPython-src-$WXPYTHON_VERSION.tar.bz2" -o wxPython.tar.bz2 && \
  mkdir /build/wxPython && \
  tar -jxvf wxPython.tar.bz2 --strip-components=1 -C /build/wxPython && \
  cd /build/wxPython/wxPython && \
  python ./build-wxpython.py --build_dir=../wxBuild && \
  python ./build-wxpython.py --install --build_dir=../wxBuild && \
  cd && rm -rf /build
