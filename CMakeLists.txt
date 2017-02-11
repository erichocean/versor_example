project (versor_example)

cmake_minimum_required (VERSION 3.1.0)

set(CMAKE_MACOSX_RPATH 1)

# Begin Versor CMake setup
set(VERSOR_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/versor)

set(VERSOR_INC
    ${VERSOR_ROOT}/include/vsr
    ${VERSOR_ROOT}/ext/glv
    ${VERSOR_ROOT}/ext/glv/GLV
    ${VERSOR_ROOT}/ext/gfx
    ${VERSOR_ROOT}/ext/gfx/gfx
)
set(VERSOR_LIB
    ${VERSOR_ROOT}/build/libvsr.a
    ${VERSOR_ROOT}/build/libvsrGfx.a
    ${VERSOR_ROOT}/ext/glv/build/lib/libGLV.a
    ${VERSOR_ROOT}/build/ext/gfx/libgfx.a
)

include_directories(${VERSOR_INC})

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(GLEW REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS} ${GLEW_INCLUDE_DIRS})
# End Versor CMake setup

# Begin example CMake setup
include_directories(".")

add_compile_options(-stdlib=libc++)
add_compile_options(-std=c++11)

SET(H_FILES
    "example.h"
)
SET(CPP_FILES
    "example.cpp"
)

SET(SOURCE_FILES ${H_FILES} ${CPP_FILES})

add_executable(example ${SOURCE_FILES})
target_link_libraries(example ${VERSOR_LIB} ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} ${GLEW_LIBRARY})
