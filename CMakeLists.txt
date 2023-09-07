cmake_minimum_required(VERSION 3.16)

# project name
project(CG-project)

#standart
set(CMAKE_CXX_STANDARD 17)

#compiler flags
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

#search glad in conan
include(${PROJECT_SOURCE_DIR}/build-conan/conan_toolchain.cmake)
find_package(glad)

add_executable(${PROJECT_NAME} main.cpp)

#added libraries
target_link_libraries(${PROJECT_NAME} glfw glad::glad)