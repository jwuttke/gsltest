cmake_minimum_required(VERSION 3.12)

project(GSL_FFT)

find_package(GSL REQUIRED)

add_executable (demo src/FFTExample.cpp)
target_include_directories(demo PUBLIC ${GSL_INCLUDE_DIR})
# target_link_directories(demo /usr/lib)
target_link_libraries(demo ${GSL_CBLAS_LIBRARY} ${GSL_LIBRARY})
