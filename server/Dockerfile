FROM debian:bullseye-20230522-slim

RUN apt update
RUN apt-get install -y \
    ffmpeg \
    git \
    gcc \
    g++ \
    make \
    unzip \
    automake \
    tclsh \
    cmake \
    pkg-config

RUN git clone --depth 1 -b develop https://gitee.com/ossrs/srs.git

WORKDIR ./srs/trunk

RUN ./configure
RUN make
RUN make install

EXPOSE 1935 1985 8080

CMD ./objs/srs -c conf/docker.conf
