FROM ubuntu:24.04

# Copy Source Files
COPY osu-micro-benchmarks-7.4.tar.gz /root/
COPY entrypoint.sh /root/
WORKDIR /root

# Install System Libraries
RUN apt update -y && apt install -y build-essential openmpi-bin openmpi-doc libopenmpi-dev

# Compile OSU-Micro-Benchmarks
RUN tar zxfv osu-micro-benchmarks-7.4.tar.gz
WORKDIR /root/osu-micro-benchmarks-7.4
RUN echo "Configuring and building OSU Micro-Benchmarks"
RUN ./configure --prefix=/usr/local/osu CC=/usr/bin/mpicc CXX=/usr/bin/mpicxx
RUN make -j4 && make install

RUN chmod +x /root/entrypoint.sh

ENV SINGULARITY_MPICH_DIR=/usr
ENV OSU_DIR=/usr/local/osu/libexec/osu-micro-benchmarks/mpi 

ENTRYPOINT [ "/root/entrypoint.sh" ]

