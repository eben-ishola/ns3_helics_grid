FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    cmake g++ git wget curl libboost-all-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN git clone https://github.com/GMLC-TDC/HELICS.git && \
    cd HELICS && mkdir build && cd build && \
    cmake .. && make -j$(nproc) && make install

COPY run-broker.sh /run-broker.sh
RUN chmod +x /run-broker.sh
CMD ["/run-broker.sh"]
