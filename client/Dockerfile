FROM debian:bullseye-20230522-slim

RUN apt update

# Boostrap deps
RUN apt-get install -y \
    git \
    make \
    pkg-config \
    flex \
    bison \
    dh-autoreconf

# Configure deps (this can be enabled or disabled by flags)
# The default include a QT interface so we use it. 
RUN apt-get install -y \
    g++ \
    lua5.2 \
    liblua5.2-dev \
    libavutil-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    liba52-dev \
    libx11-xcb-dev \
    libxcb-composite0-dev \
    libxcb-randr0-dev \
    libxcb-shm0-dev \
    libxcb-xkb-dev \
    libasound2-dev \
    qtbase5-dev \
    qtdeclarative5-dev \
    qtquickcontrols2-5-dev \
    libqt5svg5-dev \
    libqt5x11extras5-dev \
    gettext \
    qml-module-qtquick-controls \
    qml-module-qtquick-controls2 \
    qml-module-qtquick-layouts \
    qml-module-qtquick-window2 \
    libqt5gui5

RUN git clone --depth 1 -b master https://github.com/videolan/vlc.git

WORKDIR ./vlc

RUN ./bootstrap
RUN ./configure --enable-utf8
RUN make
RUN make install

# Dirty trick to run vlc as root user
RUN sed -i 's/geteuid/getppid/' ./vlc
CMD ./vlc rtmp://172.17.0.1/live/livestream
