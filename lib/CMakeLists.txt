set(lib mygsl)

set(CMAKE_FIND_LIBRARY_SUFFIXES .dll.a .lib)
find_package(GSL REQUIRED)
message(STATUS "GSL found=${GSL_FOUND} lib=${GSL_LIBRARIES} inc=${GSL_INCLUDE_DIR} version=${GSL_VERSION}")

add_library(${lib} SHARED mygsl.cpp)
target_include_directories(${lib} PUBLIC ${GSL_INCLUDE_DIR})
target_link_libraries(${lib} ${GSL_LIBRARIES}) # ${GSL_CBLAS_LIBRARY} ${GSL_LIBRARY}`)
set(${lib}_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR} PARENT_SCOPE)
set(${lib}_LIBRARY ${lib} PARENT_SCOPE)

if(WIN32)
    message(STATUS "YES WE ARE UNDER WIN32")
    install(FILES
        ${CMAKE_SOURCE_DIR}/../lib/msys-gsl.dll
        ${CMAKE_SOURCE_DIR}/../lib/msys-gslcblas.dll
        DESTINATION bin COMPONENT Libraries)
endif()
