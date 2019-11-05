FROM debian:10

ENV DEBIAN_FRONTEND=noninteractive

RUN \
  apt-get update && \
  apt-get install --yes \
    g++ make cmake unzip

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
