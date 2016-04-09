FROM debian:jessie
MAINTAINER Jonathan Brooker <jonathan.brooker@gmail.com>

RUN apt-get update \
 && apt-get install -y --no-install-recommends wget rsync cmake binutils make \
    pkg-config perl-modules libdigest-md5-file-perl xz-utils python \
 && wget -O - \
    http://llvm.org/releases/3.8.0/clang+llvm-3.8.0-x86_64-linux-gnu-debian8.tar.xz \
  | tar -C /tmp/ -xJf - \
 && rsync -a /tmp/clang+llvm-3.8.0-x86_64-linux-gnu-debian8/ /usr/local/ \
 && apt-get -y remove wget xz-utils rsync \
 && apt-get -y autoremove \
 && apt-get -y clean \
 && update-alternatives --install /usr/bin/cc cc /usr/local/bin/clang 100 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/local/bin/clang++ 100

ENTRYPOINT	[ "bash" ]
