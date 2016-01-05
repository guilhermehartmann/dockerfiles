FROM debian:jessie
MAINTAINER Jonathan Brooker <jonathan.brooker@gmail.com>

RUN apt-get update \
 && apt-get install -yy --no-install-recommends build-essential python golang \
    cmake ninja-build autoconf automake autotools-dev libtool coreutils \
    make git subversion pkg-config perl-modules libdigest-md5-file-perl libasan1 \
 && mkdir -p /src \
 && mkdir -p /build/llvm \
 && cd /src && git clone --depth 1 http://llvm.org/git/llvm.git \
 && cd /src/llvm/tools && git clone --depth 1 http://llvm.org/git/clang.git \
 && cd /src/llvm/projects && git clone --depth 1 \
    http://llvm.org/git/compiler-rt.git \
 && cd /src/llvm/projects && git clone --depth 1 \
    http://llvm.org/git/libcxx.git \
 && cd /src/llvm/projects && git clone --depth 1 \
    http://llvm.org/git/libcxxabi.git \
 && cd /build/llvm \
 && cmake -G "Ninja" -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_FLAGS="-O3" /src/llvm \
 && ninja install \
 && rm -rf /build \
 && apt-get -yy remove build-essential python golang ninja-build autoconf \
    automake autotools-dev libtool coreutils git subversion \
 && apt-get -yy autoremove \
 && apt-get -yy clean \
 && update-alternatives --install /usr/bin/cc cc /usr/local/bin/clang 100 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/local/bin/clang++ 100

ENTRYPOINT	[ "bash" ]
