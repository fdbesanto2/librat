
![linux](docs/res/ubuntu_sm.png) [![Status](https://github.com/profLewis/librat/workflows/CI%20ubuntu/badge.svg)](https://github.com/profLewis/librat/actions?query=workflow%3A%22CI+ubuntu%22)  ![macOS](docs/res/apple_sm.png) [![Status](https://github.com/profLewis/librat/workflows/CI%20macos/badge.svg)](https://github.com/profLewis/librat/actions?query=workflow%3A%22CI+macos%22). ![win](docs/res/win_sm.png) [![Status](https://github.com/profLewis/librat/workflows/CI%20windows/badge.svg)](https://github.com/profLewis/librat/actions?query=workflow%3A%22CI+windows%22)

<p align="center">
  <a href="https://github.com/profLewis/librat">
    <img src="http://www2.geog.ucl.ac.uk/~plewis/images/millet/millet.gif" alt="Millet the movie" width="72" height="72">
  </a>
</p>
<h2 align="center">librat 🐀</h2>

<p align="center">
  A ray tracing library built for radiative transfer simulations for remote sensing studies.
  <br>
  <a href="https://github.com/profLewis/librat/docs"><strong>Explore librat docs »</strong></a>
  <br>
  <br>
  <a href="https://github.com/profLewis/librat/issues/new?template=bug.md">Report bug</a>
  ·
  <a href="https://github.com/profLewis/librat/issues/new?template=feature.md&labels=feature">Request feature</a>
  ·
  <a href="https://blog.librat.com/">~~Blog~~</a>
</p>

## Table of contents

- [Quick start](#quick-start)
- [Status](#status)
- [Bugs and feature requests](#bugs-and-feature-requests)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Community](#community)
- [Versioning](#versioning)
- [Creators](#creators)
- [Thanks](#thanks)
- [Copyright and license](#copyright-and-license)


## Quick start

Several quick start options are available:

- [Download the latest release.](https://github.com/profLewis/librat/archive/master.zip)
- Clone the repo: `git clone https://github.com/profLewis/librat.git`

`librat` (actually called `ratlib` in the code ) is a ray tracing library built for radiative transfer simulations for remote sensing studies. It was originally written in the later 1980s/early 1990s by [P. Lewis](http://www2.geog.ucl.ac.uk/~plewis/), as part of his [PhD, A Botanical Plant Modelling System for Remote Sensing
Simulation Studies, UCL, 1996](http://www2.geog.ucl.ac.uk/~plewis/phd). The main advantage of this code is that it is part of a community reference effort for radiative transfer. That has been a major motivating factor in releasing the code in this (easy to use) form. It has also been used in a [wide range of studies](docs/ratindex.md).

Read the [Getting started page](https://github.com/profLewis/librat/docs/getting-started/introduction/) for information on examples, and more.


## Status



## Bugs and feature requests

Have a bug or a feature request? Please first read the [issue guidelines](https://github.com/profLewis/librat/blob/master/.github/CONTRIBUTING.md#using-the-issue-tracker) and search for existing and closed issues. If your problem or idea is not addressed yet, [please open a new issue](https://github.com/profLewis/librat/issues/new).


## Documentation

todo

### Running documentation locally


### Documentation for previous releases


## Contributing

## Community

Get updates on librat development and chat with the project maintainers and community members.

- Follow [@RayLibrat on Twitter](https://twitter.com/RayLibrat).

## Versioning

See [the Releases section of our GitHub project](https://github.com/profLewis/librat/releases) for changelogs for each release version of Bootstrap. Release announcement posts on [~~the official Bootstrap blog~~](https://blog.librat.com/) contain summaries of the most noteworthy changes made in each release.


## Creators

**Philip Lewis**

- <https://twitter.com/profplewis>
- <https://github.com/profLewis>



## Thanks


Thanks 

## Sponsors


## Backers


## Copyright and license



To set the library up on your computer, you need to configure and compile the code. As explained in more detail below, this involves typing:

    ./configure; make clean all test
    
at the shell prompt. Press the `<return>` key to execute the commands. The semicolon `;` allows us to put multiple commands on the same line. We could otherwise type them on seperate lines. 


<h4 align="center">📲Configuration</h4>



To configure this library on your computer, in a unix shell type:

    ./configure

Press the `<return>` key to execute the command. The configure script sets up the environment for your computer. The reason we type `./` in front of it, it to tell the unix interpreter that the script `configure` is in the **current working directory** which is indicated by `.`. It does this by testing that various options work on your particular setup. The range of options we have should work with most `*nix` setups. Specifically, [`configure`](configure)  sets variables from [`config.in`](config.in):

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

in the file [`src/makefile`](src/makefile). Note that [`src/makefile`](src/makefile) is generate from the template [`src/Makefile.in`](src/Makefile.in).


<h4 align="center">⏳ Compilation</h4>


To compile and test the library (after running [`./configure`)](configure), type:

    make clean all test
    
Press the `<return>` key to execute the command. In fact, if you forget to run [`./configure`)](configure), this will run it for you, via the file [`makefile`](makefile). The command `make clean` clears out any previously compiled code. Then `make all` compiles the library `${BPMS}/lib/${ARCH}/libratlib.so` (so, you refer to this as `-L ${BPMS}/lib/${ARCH} -lratlib`. It also compiles a `C` language interface to the library, `${BPMS}/bin/${ARCH}/RATstart`. `make test` runs a test on the `RATstart` code, comparing a simple ray tracing outout to a reference one.

To sum up, after compilation, you will have generated files in

* [`bin/${ARCH}`](bin/x86_64) : executable -- `RATstart`
* [`lib/${ARCH}`](lib/x86_64) : shared object library -- `libratlib.so`

Notice that these links ⛓ (`bin/x86_64`, `lib/x86_64`)  don't exist on the github repository: they are user-generated!

