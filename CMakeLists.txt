cmake_minimum_required(VERSION 3.0)
list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/Modules")

project("Calico Doom" C CXX)

add_definitions("-Wall -Wextra")

# Once CMake 3.1 is required, you can replace this with CMAKE_CXX_STANDARD
if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    set(CMAKE_CXX_FLAGS "--std=gnu++17 ${CMAKE_CXX_FLAGS}")
endif()

find_package(SDL2 REQUIRED)
find_package(SDL2_mixer REQUIRED)
if(PS2)
set (OPENGL_INCLUDE_DIRS ${PS2SDK}/ports/include)
set (OPENGL_gl_LIBRARY ${PS2SDK}/ports/lib)
else()
find_package(OpenGL)
endif()
add_subdirectory(src)
