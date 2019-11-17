FROM ubuntu:18.04

RUN apt-get update && apt-get install -y autoconf automake autotools-dev curl libmpc-dev \
    libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc \
    zlib1g-dev libexpat-dev

VOLUME /src

RUN apt-get install -y libisl-dev

WORKDIR /src

VOLUME /out
