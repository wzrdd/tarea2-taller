FROM debian:bullseye-20230522-slim

RUN apt update
RUN apt-get install -y \
    ffmpeg

COPY linger.flv /

CMD ffmpeg -stream_loop -1 -re -i linger.flv -c copy -f flv rtmp://172.17.0.1/live/livestream
