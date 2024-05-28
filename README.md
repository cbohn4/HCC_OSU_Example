OSU Benchmarks Tarball [Download](https://mvapich.cse.ohio-state.edu/benchmarks/)


# Instructions
Download the latest version of the OSU Benchmarks Tarball and extract it. Version numbers may need updated. 

## INSTALL 
```bash

tar zxf osu-micro-benchmarks-7.4.tar.gz
module purge
module load compiler/gcc/11 openmpi/4.1
cd osu-micro-benchmarks-7.4
./configure --prefix=${PWD}/osu CC=/util/opt/openmpi/4.1.5/gcc/11/bin/mpicc CXX=/util/opt/openmpi/4.1.5/gcc/11/bin/mpicxx
make -j16 && make install
```

## RUN

```bash
cd .. # Into the repository directory
sbatch osu.submit
```