FROM alpine:3

RUN apk add --no-cache \
    binutils-gold \
    g++ \
    libstdc++ \
    linux-headers \
    cmake \
    make

ADD https://github.com/quickfix/quickfix/archive/master.zip .

RUN \
  unzip master.zip && \
  rm master.zip && \
  cd quickfix-master && \
  sed -i '/add_subdirectory(examples)/d' CMakeLists.txt && \
  sed -i '/add_subdirectory(test)/d' CMakeLists.txt && \
  mkdir build && \
  cd build && \
  cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo .. && \
  make -j$(nproc) && \
  make install
