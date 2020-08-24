## General information

The goal of this project is to collect various Docker images files related to
the Ada programming language.

## Images list

At this moment available files are:

* Dockerfile.gnat - The base image with GNAT FSF version and Gprbuild for
  Linux 64bit. Based on the newest Ubuntu release.
* Dockerfile.gnatgtk - The base image with GNAT FSF version, development
  version of GtkAda library and Gprbuild for Linux 64bit. Based on the newest
  Ubuntu release.
* Dockerfile.gnattashy - The base image with GNAT FSF version, TASHY library
  and Gprbuild for Linux 64bit. Based on the newest Ubuntu release.
* Dockerfile.mingw64 - The base image with GNAT MinGW 64bit FSF version and
  Gprbuild. Based on the newest Ubuntu release.
* Dockerfile.aarch64 - The base image with GNAT FSF 10 version and Gprbuild
  for Arm64 (aarch64) architecture. Based on the stable Debian release.
* Dockerfile.gnueabihf - The base image with GNAT FSF 10 version and Gprbuild
  for armv7 (32 bit), example: Raspberry Pi. Based on the stable Debian
  release.

## Usage

To build any of this images, type in console in this same directory where files
are:

`docker build --file [filename] .`

For example, to build just gnat version, type:


`docker build --file Dockerfile.gnat .`

## Adding a new image

If you have any Docker file related to the Ada programming language:

* Clone this repo
* Add a new Docker file
* Add it here via [pull request](https://github.com/thindil/dockerada/pulls)

## License

If not specified another, all Docker files are released under Apache 2.0
license

----

That's all for now, if you have any question, ideas or request, feel free to
use the project issues :)

Bartek thindil Jasicki
