## General information

The goal of this project is to collect various Docker images files related to
the Ada programming language.

## Images list

At this moment available images are:

### GNAT

The base image with GNAT FSF version and gprbuild for Linux 64bit. Based on
the newest Ubuntu release. Using this doesn't require any special settings.
Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat:2020.1 bin/sh -c "gprbuild -P myproject.gpr"`

### GNAT-Gtk

The base image with GNAT FSF version, development version of GtkAda library
and gprbuild for Linux 64bit. Based on the newest Ubuntu release. Same as
the standard GNAT image, this doesn't require any special settings. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnatgtk:2020.1 bin/sh -c "gprbuild -P myproject.gpr"`

### GNAT-Mingw64
The base image with GNAT MinGW 64bit FSF version and gprbuild. Based on the
newest Ubuntu release. If you want to use any additional libraries, you will
need to build them by yourself. At this moment this image wasn't too good
tested, thus please report any problems with it. To use it, you will need to
setup `--target=x86_64-windows`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-mingw64:2020.1 bin/sh -c "gprbuild -P myproject.gpr --target=x86_64-windows"`

### GNAT-ARM64

The base image with GNAT FSF version and gprbuild for Arm64 (aarch64)
architecture. Based on the stable Debian release. If you want to use any
additional library, you have to install it with suffix `:arm64`. Example:
`apt install tcl-dev:arm64`. To use it, you will need to setup
`--target=aarch64-linux-gnu`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-arm64:2020.1 bin/sh -c "gprbuild -P myproject.gpr --target=aarch64-linux-gnu"`

### GNAT-ARMv7

The base image with GNAT FSF version and gprbuild for armv7 (32 bit),
example: Raspberry Pi. Based on the stable Debian release. If you want to use
any additional library, you have to install it with suffix `:armhf`.
Example: `apt install libgtkada-dev:armhf`. To use it, you will need to setup
`--target=arm-linux-gnueabihf`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-arm7:2020.1 bin/sh -c "gprbuild -P myproject.gpr --target=arm-linux-gnueabihf"`

### Ada-Build

This is extended image for build some of my projects for Linux 64-bit. It
contains:
- GNAT FSF version
- gprbuild
- Tashy (and Tcl and Tk libraries)
- libmagic-dev
- libxmlada-schema9-dev
- libxmlada-input9-dev
Example usage:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/adabuild:2020.1 bin/sh -c "gprbuild -P myproject.gpr"`

## Usage

To build any of this images, type in console in this same directory where files
are:

`docker build --file [filename] .`

For example, to build just gnat version, type:

`docker build --file Dockerfile.gnat .`

You can also download some prepared images. They are available here:

https://github.com/thindil?tab=packages

Navigate to the selected Docker image to get more information how to use them.

## Adding a new image

If you have any Docker file related to the Ada programming language:

* Clone this repo
* Add a new Docker file
* Add it here via [pull request](https://github.com/thindil/dockerada/pulls)

## FAQ

Q: Why arm64 and armv7 images are based on Debian?

A: At this moment (2020-08) Ubuntu has problems with properly support both
architectures: some repositories are not available or missing. In that
situation it is easier to build/extend Docker image from Debian than from
Ubuntu.

Q: Why not use Docker buildx for build multiarch images?

A: While in 90% of situations buildx multiarch Docker images works in the rest
10% they fails miserably. And this 10% is exactly GCC/GNAT situation. Buildx
Docker images are extremely slow (even 15-30 times slower) compared to native
or cross compilation. This is probably related to use Qemu in them. Even using
Quemu-Kvm not helps. This is why in these images are used cross-compilers.

## License

If not specified another, all Docker files are released under Apache 2.0
license

----

That's all for now, if you have any question, ideas or request, feel free to
use the project issues (even if you want to talk about the project
organization or lack of it) :)

Bartek thindil Jasicki
