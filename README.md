Before you go further, if you haven't already, install `glew`:

    brew install glew

# Usage

To use the Versor library as an external project with CMake, clone this repository,
then build Versor as follows:

    # clone this project
    git clone https://github.com/erichocean/versor_example.git
    cd versor_example
    
    # clone and build Versor
    git clone https://github.com/wolftype/versor.git
    cd versor
    git submodule update --init
    ./build.sh
    cd ..

From this point on, it's irrelevant that we just used CMake to build Versor. Versor
could have been built using any build system (Make, Bazel, etc). *All we care about
now is the location of the built static archives and the include directories.*

With Versor now built, you can compile the example Versor app using CMake:

    mkdir build
    cd build
    cmake ..
    make
    ./example

To repeat, the "trick" is just to set up the `CMakeLists.txt` correctly with the
location of the external libraries/includes. If you look in the top-level
`CMakeLists.txt` file, you can see how I did that. There are other ways to link an
external library with CMake, but I find this is the easiest.

Best, Erich
