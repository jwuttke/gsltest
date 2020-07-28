cmake_minimum_required(VERSION 3.12)

project(GSL_FFT)

SET( CMAKE_CXX_COMPILER "/usr/bin/g++" )
SET(CMAKE_CXX_FLAGS "-std=c++11 -Wuninitialized -Wunused-function -Wunused-label -Wunused-value -Wunused-variable")

include_directories(src)

link_directories(/usr/lib)

add_executable (FFTExample src/FFTExample.cpp)

target_link_libraries(FFTExample gsl gslcblas)
