cmake_minimum_required(VERSION 3.13)
project(example-grpc LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

execute_process(COMMAND conan install .. --build=missing)
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)
include(${CMAKE_CURRENT_BINARY_DIR}/conan_paths.cmake)


find_package(protobuf REQUIRED)
find_package(gRPC REQUIRED)


# target_link_libraries(${target_name} ${CONAN_LIBS})
# foreach(v ${CONAN_LIBS})
# message(${v})
# endforeach()

add_subdirectory(client)
add_subdirectory(server)
add_subdirectory(proto)
