FROM ubuntu:14.04
MAINTAINER Jonathan Brooker <jonathan.brooker@gmail.com>

RUN apt-get update \
 && apt-get install -y \
            wget \
            libcairo2 \
            libxcb-icccm4 \
            libxcb1 \
            libxcb-randr0 \
            libx11-xcb1 \
            libxkbfile1 \ 
            libxcursor1 \
            libstdc++6 \
            libc6 \
            libgcc1 \
            libpixman-1-0 \
            libfontconfig1 \ 
            libfreetype6 \
            libpng12-0 \
            libxcb-shm0 \
            libxcb-render0 \
            libx11-6 \
            zlib1g \
            libxau6 \
            libxdmcp6 \
            libxfixes3 \
            libexpat1 \
            libxrender1 \
            libx11-6 \
            zlib1g \
            libjack-jackd2-0 \
            xdg-utils \
            libav-tools \
            zenity \
            links \
  && wget http://downloads.bitwig.com/stable/1.3.6/bitwig-studio-1.3.6.deb \
  && dpkg -i bitwig-studio-1.3.6.deb \
  && rm bitwig-studio-1.3.6.deb \
  && apt-get -y remove wget \
  && apt-get -y autoremove \
  && apt-get -y clean

ENTRYPOINT [ "bitwig-studio" ]
