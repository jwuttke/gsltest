cmake_minimum_required(VERSION 3.12)

project(GSL_FFT)

if(WIN32)
set(GSL_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/../include)
set(GSL_CBLAS_LIBRARY ${CMAKE_SOURCE_DIR}/../lib/libgslcblas.dll.a)
set(GSL_LIBRARY ${CMAKE_SOURCE_DIR}/../lib/libgsl.dll.a)

else()
find_package(GSL REQUIRED)
endif()

add_executable (demo src/FFTExample.cpp)
target_include_directories(demo PUBLIC ${GSL_INCLUDE_DIR})
# target_link_directories(demo /usr/lib)
target_link_libraries(demo ${GSL_CBLAS_LIBRARY} ${GSL_LIBRARY})
