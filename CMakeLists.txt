cmake_minimum_required(VERSION 3.25 FATAL_ERROR)

set (CMAKE_CXX_STANDARD 20)
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

project(librdmapp LANGUAGES CXX)

#TODO: Add numa,rdma,ib as deps

file(GLOB SRC_FILES ./rdmapp/*.cpp)
add_library(librdmapp STATIC ${SRC_FILES})
