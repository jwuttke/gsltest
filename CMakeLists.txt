cmake_minimum_required(VERSION 3.12)

project(GSL_FFT)

find_package(GSL REQUIRED)
message(STATUS "GSL found=${GSL_FOUND} lib=${GSL_LIBRARIES} inc=${GSL_INCLUDE_DIR} version=${GSL_VERSION}")

add_executable (demo src/FFTExample.cpp)
target_include_directories(demo PUBLIC ${GSL_INCLUDE_DIR})
target_link_libraries(demo ${GSL_CBLAS_LIBRARY} ${GSL_LIBRARY})

if(WIN32)
    message(STATUS "YES WE ARE UNDER WIN32")
    install(FILES
        ${CMAKE_SOURCE_DIR}/../lib/msys-gsl.dll
        ${CMAKE_SOURCE_DIR}/../lib/msys-gslcblas.dll
        DESTINATION bin COMPONENT Libraries)
    install(TARGETS demo DESTINATION bin COMPONENT Applications)
endif()
