# add cpp files to the test cases
add_executable(test_rdma test_rdma.cpp)
add_dependencies(test_rdma rdmapp)

target_compile_options(test_rdma PRIVATE -pthread -lrdmacm)

include_directories(${VERBS_INCLUDE_DIR})

target_link_libraries(test_rdma rdmapp -pthread -libverbs -lrdmacm)

