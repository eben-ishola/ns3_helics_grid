FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    git cmake g++ curl libboost-all-dev \
    python3 python3-dev python3-pip \
    make \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN git clone https://github.com/gridlab-d/gridlab-d.git && \
    cd gridlab-d && mkdir build && cd build && \
    cmake .. && \
    make -j$(nproc) && \
    make install

COPY run-simulation.sh /run-simulation.sh
RUN chmod +x /run-simulation.sh
CMD ["/run-simulation.sh"]
