cmake_minimum_required(VERSION 3.12)

project(GSL_FFT)

set(CMAKE_FIND_LIBRARY_SUFFIXES .dll.a .lib)
find_package(GSL REQUIRED)
message(STATUS "GSL found=${GSL_FOUND} lib=${GSL_LIBRARIES} inc=${GSL_INCLUDE_DIR} version=${GSL_VERSION}")

add_subdirectory(lib)
add_subdirectory(src)
