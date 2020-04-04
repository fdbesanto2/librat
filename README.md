# librat
librat

Installation
============

To set this up, in a unix shell type:

    ./configure
    make clean all test

The configure script sets variables from config.in:

    set CCS = ("gcc" "cc")
    set CFLAGSS = ("-I." "-fPIC")
    set DYNS = ("ld -G" "libtool  -L.. -lc -dynamic -undefined dynamic_lookup")
    set MAKES = ("gmake" "make")
    set OPTS = ("-g")
    # specify a temporary directory
    set TMP = /tmp
    
These are the options considered in configure. For example, we first try a compiler `gcc` and if that fails, try `cc`. We try ther dynamic linker `ld -G` and if that fails, `libtool  -L.. -lc -dynamic -undefined dynamic_lookup` etc. Note that the configutaion will settle on the first option in the list that passes some internal tests (follow through the script [`configure`](configure)).

The configuation the sets e.g. (settings on `OS X x86_64`):

    ARCH = x86_64
    OBJ = objects.${ARCH}

    BPMS = /Users/plewis/librat
    LIB = ${BPMS}/lib
    BIN = ${BPMS}/bin

    CFLAGS = -I.
    MAKE = make
    WG = -L -R --create-dirs -o
    WGET = /usr/bin/curl
    CC = gcc
    DYN = libtool -L.. -lc -dynamic -undefined dynamic_lookup
    OPT = -g

in the file `src/makefile`. Note that `src/makefile` is generate from `src/Makefile.in`.

Compilation
===========

To compile and test the library (aftyer running `./configure`), type:

    make clean all test
    
as above. In fact, if you forget to run `./configure`, this will run it for you, via the file `makefile`. The `make clean` clears out any previouysly compiled code. Then `make all` compiles the library `${BPMS}/lib/${ARCH}/libratlib.so` (so, you refer to this as `-L ${BPMS}/lib/${ARCH} -lratlib`. It also compiles a `C` language interface to the library, `${BPMS}/bin/${ARCH}/start`. `make test` runs a test on the `start` code, comparing a simple ray tracing outout to a reference one.


