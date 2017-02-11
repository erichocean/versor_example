If you haven't already, install `glew`:

    brew install glew

To use the Versor library an an external project, clone this repository, then:

    cd versor_example
    git clone https://github.com/wolftype/versor.git
    cd versor
    git submodule update --init
    ./build.sh
    cd ..

Now that `versor` is built, you can compile the example:

    mkdir build
    cd build
    cmake ..
    make
    ./example

The "trick" is just to set up CMake correctly with an external project. If
you look in the top-level `CMakeLists.txt` file, you can see how I did that.
There are other ways to do this, but I find this is the easiest.

Best, Erich