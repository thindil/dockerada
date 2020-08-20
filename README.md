## General information

The goal of this project is to collect various Docker images files related to
the Ada programming language. All images are based on the newest Ubuntu release
and use the default version of GNAT FSF (default related to GCC and the
selected Ubuntu release)

## Images list

At this moment available files are:

* Dockerfile.gnat - The base image with GNAT FSF version and Gprbuild
* Dockerfile.gnatgtk - The base image with GNAT FSF version, development
  version of GtkAda library and Gprbuild
* Dockerfile.gnattashy - The base image with GNAT FSF version, TASHY library
  and Gprbuild
* Dockerfile.mingw64 - The base image with GNAT MinGW 64bit FSF version and
  Gprbuild

## Usage

To build any of this images, type in console in this same directory where files
are:

`docker build --file [filename] .`

For example, to build just gnat version, type:


`docker build --file Dockerfile.gnat .`

## License

If not specified another, all Docker files are released under Apache 2.0
license

----

That's all for now, if you have any question, ideas or request, feel free to
use the project issues :)

Bartek thindil Jasicki
