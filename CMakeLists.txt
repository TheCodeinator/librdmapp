cmake_minimum_required(VERSION 3.25 FATAL_ERROR)

project(librdmapp LANGUAGES CXX)

set (CMAKE_CXX_STANDARD 20)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

find_package(Threads REQUIRED)

include_directories(${NUMA_PATH}/**)

file(GLOB SRC_FILES ./rdmapp/*.cpp)
add_library(rdmapp STATIC ${SRC_FILES})

target_link_libraries(rdmapp -pthread -libverbs -lrdmacm)
# just to be sure :) 
set_property(TARGET rdmapp PROPERTY CXX_STANDARD 20)

# add tests
add_subdirectory(tests)
