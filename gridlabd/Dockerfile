FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    gridlabd git cmake g++ curl libboost-all-dev && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /opt

RUN git clone https://github.com/GMLC-TDC/HELICS.git && \
    cd HELICS && mkdir build && cd build && \
    cmake .. && make -j$(nproc) && make install

COPY run-simulation.sh /run-simulation.sh
RUN chmod +x /run-simulation.sh
CMD ["/run-simulation.sh"]
