# Modern C++ Template

This is a template that can be used to start developing a project in C++. We use [conan](https://conan.io/) as
package manager.

## Build and run

We need some additional tools in order to build it (besides the usual C++ compiler). In particular,
please make sure to install:

- Conan 2. You can find the official documentation [here](https://docs.conan.io/2/installation.html).
- CMake and Make. For example in an Ubuntu system, the latter can be installed simply with `sudo apt install make`.

Once both of them are installed, you simply need to execute:

```shell
mkdir build && cd build
cmake -DCMAKE_PROJECT_TOP_LEVEL_INCLUDES=conan_provider.cmake ..
make
```

Now, you should find the binary inside `build/app/`.

## Docker

You can use the `Dockerfile` provided by us to create an image in which to build and run the code. So first, build
the image:

```shell
docker build -t my_image .
```

Then you can start it and compile/run the code:

```shell
docker run --rm -it -v .:/my_code my_image bash
mkdir /my_code/build && cd /my_code/build
cmake -DCMAKE_PROJECT_TOP_LEVEL_INCLUDES=conan_provider.cmake ..
make
```