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
    clang-tidy-3.8 lldb-3.8 cmake make pkg-config perl-modules \
    libdigest-md5-file-perl \
 && wget -O - \
    https://www.dropbox.com/s/7w8121wwnvjn861/clanglibs.3.8.0.tar.gz?dl=0 \
  | tar -C /usr/lib/llvm-3.8/lib/clang/3.8.0/lib/linux/ -xzf - \
 && apt-get -yy remove wget \
 && apt-get -yy autoremove \
 && apt-get -yy clean \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-format /usr/bin/clang-format \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-check  /usr/bin/clang-check \
 && ln -sf /usr/lib/llvm-3.8/bin/clang-tidy   /usr/bin/clang-tidy \
 && ln -sf /usr/lib/llvm-3.8/bin/clang        /usr/bin/clang \
 && ln -sf /usr/lib/llvm-3.8/bin/clang++      /usr/bin/clang++ \
 && ln -sf /usr/bin/scan-build-3.8            /usr/bin/scan-build \
 && ln -sf /usr/bin/scan-view-3.8             /usr/bin/scan-view \
 && update-alternatives --install /usr/bin/cc cc /usr/bin/clang 100 \
 && update-alternatives --install /usr/bin/c++ c++ /usr/bin/clang++ 100

ENTRYPOINT	[ "bash" ]
