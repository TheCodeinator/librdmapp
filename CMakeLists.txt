cmake_minimum_required(VERSION 3.25 FATAL_ERROR)

set (CMAKE_CXX_STANDARD 20)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

project(librdmapp LANGUAGES CXX)

find_package(Threads REQUIRED)

include_directories(${NUMA_PATH}/**)

file(GLOB SRC_FILES ./rdmapp/*.cpp)
add_library(rdmapp STATIC ${SRC_FILES})

target_link_libraries(rdmapp -pthread -libverbs -lrdmacm)

# add tests
add_subdirectory(tests)
