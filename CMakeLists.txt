CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
project("Nome do Projeto" CXX)


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


# find_package(OpenMP)
# if (OPENMP_FOUND)
#     set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
# endif(OPENMP_FOUND)

SET(CMAKE_VERBOSE_MAKEFILE on)
if(CMAKE_BUILD_TYPE MATCHES DEBUG)
	MESSAGE(STATUS "Debug mode")
    SET(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -std=c++11 -Wall -Wl,--no-as-needed")
	SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${CMAKE_CXX_FLAGS_DEBUG}")
else()
	MESSAGE(STATUS "Release mode")
    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -std=c++11 -Wall -Wl,--no-as-needed")
	SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${CMAKE_CXX_FLAGS_RELEASE}")
endif(CMAKE_BUILD_TYPE MATCHES DEBUG)


add_custom_target(headerfiles SOURCES
     include/foo.hpp
)

include_directories(${CMAKE_SOURCE_DIR}/include)
link_directories(${CMAKE_SOURCE_DIR}/lib)

add_subdirectory(${CMAKE_SOURCE_DIR}/src)
add_subdirectory(${CMAKE_SOURCE_DIR}/test)
add_subdirectory(${CMAKE_SOURCE_DIR}/lib)
add_subdirectory(${CMAKE_SOURCE_DIR}/benchmark)
