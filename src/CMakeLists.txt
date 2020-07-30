add_executable (demo main.cpp)
target_include_directories(demo PUBLIC ${mygsl_INCLUDE_DIRS})
target_link_libraries(demo mygsl) # ${GSL_CBLAS_LIBRARY} ${GSL_LIBRARY})

if(WIN32)
    message(STATUS "YES WE ARE UNDER WIN32")
    install(TARGETS demo DESTINATION bin COMPONENT Applications)
endif()
