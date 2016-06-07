#Python 2.7 with wxpython and omniorb
FROM cromo/omniorbhy

ENV OMNIORB_VERSION 4.2.1

mkdir /build && \
cd /build && \
curl -SL "http://sourceforge.net/projects/wxpython/files/wxPython/$WXPYTHON_VERSION/wxPython-src-$WXPYTHON_VERSION.tar.bz2" -o wxPython.tar.bz2 && \
mkdir /build/wxPython && \
tar -jxvf wxPython.tar.bz2 --strip-components=1 -C /build/wxPython && \
cd /build/wxPython/wxPython && \
python ./build-wxpython.py --build_dir=../wxBuild && \
python ./build-wxpython.py --install --build_dir=../wxBuild && \
cd && rm -rf /build
