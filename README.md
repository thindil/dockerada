## Table of Contents
* [General information](#general-information)
* [Versioning](#versioning)
* [Images List](#images-list)
* [Usage](#usage)

## General information

The goal of this project is to collect various Docker images files (and images
themselves) related to the Ada programming language. **Note:** Old versions of
images (marked as *deprecated*) require Github account to download. Newer
versions are available for everyone. If you read this file on Github:
**please don't send pull requests here**. All will be automatically closed.
Any code propositions should go to the [Fossil](https://www.laeran.pl/repositories/dockerada)
repository.

## Versioning

Each image uses as the version number the number of major version of the GNAT.
Thus for example, *gnatgtk:9* means that image is based on the GNAT version 9.x

## Images list

At this moment available images are:

### GNAT

The base image with GNAT FSF version and gprbuild for Linux 64bit. Based on
the newest Ubuntu release. Using this doesn't require any special settings.
Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat:9 bin/sh -c "gprbuild -P myproject.gpr"`

### GNAT-Gtk

The base image with GNAT FSF version, development version of GtkAda library
and gprbuild for Linux 64bit. Based on the newest Ubuntu release. Same as
the standard GNAT image, this doesn't require any special settings. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnatgtk:9 bin/sh -c "gprbuild -P myproject.gpr"`

### GNAT-Mingw64
The base image with GNAT MinGW 64bit FSF version and gprbuild. Based on the
newest Ubuntu release. If you want to use any additional libraries, you will
need to build them by yourself. At this moment this image wasn't too good
tested, thus please report any problems with it. To use it, you will need to
setup `--target=x86_64-windows`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-mingw64:9 bin/sh -c "gprbuild -P myproject.gpr --target=x86_64-windows"`

### GNAT-ARM64

The base image with GNAT FSF version and gprbuild for Arm64 (aarch64)
architecture. Based on the testing Debian release. If you want to use any
additional library, you have to install it with suffix `:arm64`. Example:
`apt install tcl-dev:arm64`. To use it, you will need to setup
`--target=aarch64-linux-gnu`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-arm64:9 bin/sh -c "gprbuild -P myproject.gpr --target=aarch64-linux-gnu"`

### GNAT-ARMv7

The base image with GNAT FSF version and gprbuild for armv7 (32 bit),
example: Raspberry Pi. Based on the testing Debian release. If you want to use
any additional library, you have to install it with suffix `:armhf`.
Example: `apt install libgtkada-dev:armhf`. To use it, you will need to setup
`--target=arm-linux-gnueabihf`. Example:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/gnat-arm7:9 bin/sh -c "gprbuild -P myproject.gpr --target=arm-linux-gnueabihf"`

### Ada-Build

This is extended image for build some of my projects for Linux 64-bit. It
contains:
- GNAT FSF version
- gprbuild
- Tcl
- Tashy (and Tcl and Tk libraries for Windows)
- libmagic-dev
- libxmlada-schema9-dev
- libxmlada-input9-dev
- asis-programs (gnattest, gnatpp, etc)

Example usage:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/adabuild:9 bin/sh -c "gprbuild -P myproject.gpr"`

### Ada-Build-Windows64

This is extended image for build some of my projects for Windows 64-bit. It
contains:
- GNAT FSF version
- gprbuild
- Tashy (and Tcl and Tk libraries)
- XmlAda

Example usage:

`sudo docker run -v $(pwd):/app ghcr.io/thindil/adabuildwin64:9 bin/sh -c "gprbuild -P myproject.gpr --target=x86_64-windows"`

## Usage

To build any of this images, type in console in this same directory where files
are:

`docker build --file [filename] .`

For example, to build just gnat version, type:

`docker build --file Dockerfile.gnat .`

You can also download some prepared images. They are available here:

https://github.com/thindil?tab=packages

Navigate to the selected Docker image to get more information how to use them.
