FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && apt-get install -y \
    git cmake g++ curl \
    libboost-all-dev \
    python3 python3-dev python3-pip \
    make autoconf automake libtool \
    libxerces-c-dev \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /opt

# Clone GridLAB-D
RUN git clone --recurse-submodules https://github.com/gridlab-d/gridlab-d.git

WORKDIR /opt/gridlab-d

# Build with cmake
RUN mkdir build && cd build && \
    cmake .. -DCMAKE_BUILD_TYPE=Release && \
    make -j$(nproc) && \
    make install

# Copy run script
COPY run-simulation.sh /run-simulation.sh
RUN chmod +x /run-simulation.sh

CMD ["/run-simulation.sh"]
