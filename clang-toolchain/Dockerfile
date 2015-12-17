FROM debian:jessie
MAINTAINER Jonathan Brooker <jonathan.brooker@gmail.com>

RUN apt-get update \
 && apt-get install -yy --no-install-recommends wget \
 && wget -O - http://llvm.org/apt/llvm-snapshot.gpg.key | apt-key add - \
 && printf "deb http://llvm.org/apt/jessie/ llvm-toolchain-jessie main" \
    > /etc/apt/sources.list.d/llvm.list \
 && cat /etc/apt/sources.list.d/llvm.list \
 && apt-get update \
 && apt-get install -yy --no-install-recommends clang-3.8 clang-format-3.8 \
    clang-tidy-3.8 lldb-3.8 cmake make pkg-config \
 && apt-get -yy remove wget \
 && apt-get -yy autoremove \
 && apt-get -yy clean \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-format /usr/bin/clang-format \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-check /usr/bin/clang-check \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-tidy /usr/bin/clang-tidy \
 && ln -sf /usr/lib/llvm-3.8/bin/clang /usr/bin/clang \
 && ln -sf /usr/lib/llvm-3.8/bin/clang++ /usr/bin/clang++ \
 && update-alternatives --install /usr/bin/cc cc /usr/bin/clang 100 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++ 100

ENTRYPOINT	[ "bash" ]
