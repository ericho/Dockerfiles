#
# To run this image:
# docker run -e \
#    DISPLAY=$DISPLAY \
#    -v /tmp/.X11-unix:/tmp/.X11-unix \
#    --device /dev/dri \
#    --device /dev/snd:/dev/snd \
#    erichcm/liberation-circuit

FROM ubuntu:16.04
LABEL maintainer "Erich Cordoba <erich.cm@yandex.com>"

RUN apt-get update && apt-get install -y liballegro5-dev build-essential git

RUN git clone https://github.com/linleyh/liberation-circuit.git /src
WORKDIR /src/
RUN ./do && cp src/g_game bin/

ENV HOME /home/liberation
RUN useradd --create-home --home-dir $HOME liberation \
    && chown -R liberation:liberation $HOME \
    && usermod -a -G audio,video liberation

USER liberation

WORKDIR /src/bin/
ENTRYPOINT [ "./g_game" ]

