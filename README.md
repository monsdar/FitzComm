# FitzComm
This is a simple Protobuf-based protocol to share information about fitness ergometers. In addition to the proto-files it has generated C++ and Python classes. It also includes a simple build-system to generate a library from the C++ classes.

## Build
This project uses [CMake](https://cmake.org) and [Conan.io](https://www.conan.io/) to provide an easy to use, portable build system. After setting up CMake and Conan on your system building works like the following:

The following could be used to build everything on a Windows machine with Visual Studio 2013:
```
cd FitzComm
mkdir build && cd build
conan install ../
cmake .. -G "Visual Studio 12 Win64"
cmake --build . --config Release --target Install
```
