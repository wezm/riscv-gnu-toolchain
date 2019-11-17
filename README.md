RISC-V GNU Compiler Toolchain
=============================

This is the RISC-V C and C++ cross-compiler.

###  Getting the sources

**Note:** This repository uses submodules:

    $ git clone https://github.com/wezm/riscv-gnu-toolchain.git
    $ cd riscv-gnu-toolchain
    $ git submodule update --init

### Prerequisites

Building requires Docker or Podman. Build the docker image with:

    docker build -t riscv-nuclei-elf-toolchain -f docker/Dockerfile docker

### Building (Newlib)

To build the Newlib cross-compiler, you must have cloned the code and built the
docker image as above. Run the build in a container. The result is written to
the `out` directory:

    docker run --rm -it -v $(pwd):/src -v $(pwd)/out:/out riscv-nuclei-elf-toolchain docker/build-newlib

You should now be able to use `riscv64-unknown-elf-gcc` and friends.

### Test Suite (Untested in this fork)

The DejaGnu test suite has been ported to RISC-V.  This can run with GDB
simulator for elf toolchain or Qemu for linux toolchain, and GDB simulator
doesn't support floating-point.
To test GCC, run the following commands:

    ./configure --prefix=$RISCV --disable-linux --with-arch=rv64ima # or --with-arch=rv32ima
    make newlib
    make report-newlib

    ./configure --prefix=$RISCV
    make linux
    make report-linux
